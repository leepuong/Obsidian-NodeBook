

# 📖 Giải Thích: zk-SNARK Demo — Multiply Circuit

  

> File này giải thích toàn bộ dự án bằng tiếng Việt, từ khái niệm đến code.

  

---

  

## 1. zk-SNARK là gì?

  

**zk-SNARK** = **Z**ero-**K**nowledge **S**uccinct **N**on-interactive **AR**gument of **K**nowledge

  

Đây là một kỹ thuật mật mã cho phép:

  

> **"Người chứng minh (Prover) có thể thuyết phục Người xác minh (Verifier) rằng họ biết một bí mật, mà không cần tiết lộ bí mật đó."**

  

### Ví dụ thực tế

  

Tưởng tượng bạn muốn chứng minh bạn biết mật khẩu vào một tòa nhà, nhưng không muốn nói mật khẩu ra. zk-SNARK cho phép bạn tạo ra một **bằng chứng toán học** (proof) để người khác kiểm tra mà không biết mật khẩu đó là gì.

  

### Trong project này

  

```

Bí mật: a = 3, b = 5

Tuyên bố công khai: c = 15

  

Prover chứng minh: "Tôi biết a và b sao cho a × b = 15"

Verifier xác nhận: "Đúng!" — mà không biết a=3 hay b=5

```

  

---

  

## 2. Các tính chất của Groth16

  

Project dùng **Groth16** — thuật toán zk-SNARK phổ biến nhất:

  

| Tính chất | Ý nghĩa |

|---|---|

| **Zero-Knowledge** | Verifier không học được gì về a hoặc b |

| **Soundness** | Không thể tạo proof giả — bất khả thi về mặt tính toán |

| **Succinctness** | Proof rất nhỏ (chỉ 3 điểm trên đường cong elliptic, ~1KB) |

| **Non-interactive** | Prover gửi proof 1 lần, không cần trao đổi qua lại |

  

---

  

## 3. Circuit — "Bản thiết kế" của bài toán

  

### Circuit là gì?

  

Trong zk-SNARK, bạn phải mô tả bài toán dưới dạng một **mạch toán học** (circuit). Circuit xác định "những ràng buộc (constraints) nào phải được thỏa mãn".

  

### Circuit của project (`multiply.circom`)

  

```circom

pragma circom 2.0.0;

  

template Multiply() {

    signal input a;    // Private — chỉ prover biết

    signal input b;    // Private — chỉ prover biết

    signal output c;   // Public  — verifier thấy được

  

    c <== a * b;       // Ràng buộc duy nhất: c phải bằng a × b

}

  

component main = Multiply();

```

  

**Giải thích từng dòng:**

  

- `signal input a/b` → **witness** (nhân chứng bí mật) — prover cung cấp khi tạo proof

- `signal output c` → **public input** — cả hai bên đều biết

- `c <== a * b` → ký hiệu `<==` có 2 tác dụng:

  1. Gán giá trị: `c = a * b`

  2. Thêm ràng buộc R1CS: `c phải bằng a * b` (không thể gian lận!)

  

### R1CS là gì?

  

**R1CS (Rank-1 Constraint System)** là dạng biểu diễn toán học của circuit.  

Mỗi constraint có dạng: `(A · witness) × (B · witness) = (C · witness)`

  

Circuit của ta có đúng **1 constraint**:

```

(1·a) × (1·b) = (1·c)

→ a × b = c

```

  

---

  

## 4. Trusted Setup — "Lễ nghi khởi tạo"

  

Groth16 yêu cầu một bước khởi tạo đặc biệt gọi là **Trusted Setup**.

  

### Tại sao cần setup?

  

Setup tạo ra các tham số mật mã phục vụ cho việc tạo và xác minh proof. Trong quá trình này có **"toxic waste"** (chất độc) — là những số ngẫu nhiên trung gian. Nếu ai đó biết toxic waste, họ có thể tạo proof giả!

  

### Giải pháp: Powers of Tau Ceremony (Multi-party Setup)

  

```

Phase 1 — Powers of Tau (không phụ thuộc vào circuit cụ thể):

  Alice đóng góp randomness → xóa toxic waste phần Alice

  Bob   đóng góp randomness → xóa toxic waste phần Bob

  ...

  → Chỉ cần 1 người thật sự xóa toxic waste là đủ an toàn!

  

Phase 2 — Gắn với circuit cụ thể:

  Lấy kết quả Phase 1 + multiply.r1cs → Proving Key + Verification Key

```

  

### Kết quả của Setup

  

| File | Ai dùng | Mục đích |

|---|---|---|

| `multiply_final.zkey` | Prover | Tạo proof |

| `verification_key.json` | Verifier | Xác minh proof (share công khai được) |

| `pot_final.ptau` | Trung gian | Kết quả Phase 1 |

  

---

  

## 5. Luồng hoạt động đầy đủ

  

```

┌─────────────────────────────────────────────────────────────┐

│                   BƯỚC 1: BIÊN DỊCH CIRCUIT                 │

│                                                             │

│  multiply.circom ──[circom compiler]──► multiply.r1cs       │

│                                     ──► multiply.wasm       │

│                                                             │

│  .r1cs = hệ phương trình ràng buộc (R1CS)                  │

│  .wasm = chương trình tính witness (chạy trên WebAssembly)  │

└─────────────────────────────────────────────────────────────┘

                              ↓

┌─────────────────────────────────────────────────────────────┐

│                   BƯỚC 2: TRUSTED SETUP                     │

│                                                             │

│  Phase 1: Powers of Tau ceremony                           │

│    newAccumulator() → Alice.contribute() → preparePhase2()  │

│    → pot_final.ptau                                         │

│                                                             │

│  Phase 2: Gắn với multiply.r1cs                            │

│    zKey.newZKey(r1cs, ptau) → Bob.contribute()              │

│    → multiply_final.zkey  +  verification_key.json          │

└─────────────────────────────────────────────────────────────┘

                              ↓

┌─────────────────────────────────────────────────────────────┐

│                   BƯỚC 3: TẠO PROOF (Prover)                │

│                                                             │

│  Input bí mật: { a: 3, b: 5 }                              │

│                                                             │

│  groth16.fullProve(                                         │

│    { a: "3", b: "5" },   ← bí mật của prover               │

│    multiply.wasm,         ← tính witness                    │

│    multiply_final.zkey    ← proving key                     │

│  )                                                          │

│                                                             │

│  → proof.json   (3 điểm elliptic curve: pi_a, pi_b, pi_c)  │

│  → public.json  (public signal: [15])                       │

└─────────────────────────────────────────────────────────────┘

                              ↓

┌─────────────────────────────────────────────────────────────┐

│                   BƯỚC 4: XÁC MINH (Verifier)               │

│                                                             │

│  Verifier có:  proof.json + public.json + vkey.json         │

│  Verifier KHÔNG có: a hoặc b                               │

│                                                             │

│  groth16.verify(vKey, [15], proof) → true / false           │

│                                                             │

│  Nếu true: "Ai đó thật sự biết a,b sao cho a×b = 15" ✓    │

└─────────────────────────────────────────────────────────────┘

```

  

---

  

## 6. Proof trông như thế nào? (`build/proof.json`)

  

```json

{

  "pi_a": ["12345...abc", "67890...def", "1"],

  "pi_b": [["aabb...cc", "ddee...ff"], ["1122...33", "4455...66"], ["1", "0"]],

  "pi_c": ["9988...77", "6655...44", "1"],

  "protocol": "groth16",

  "curve": "bn128"

}

```

  

- `pi_a`, `pi_b`, `pi_c` là **3 điểm trên đường cong elliptic BN128**

- Nhìn vào proof → KHÔNG thể tính ngược ra a hoặc b

- Verifier dùng **phép kiểm tra pairing** để xác nhận proof hợp lệ

  

---

  

## 7. Tại sao Verify lại nhanh hơn Prove?

  

| Tác vụ | Thời gian | Lý do |

|---|---|---|

| **Prove** | ~vài giây | Phải tính witness + nhiều phép nhân elliptic curve |

| **Verify** | ~mili giây | Chỉ kiểm tra 3 phép pairing cố định |

  

Đây là tính chất **"Succinct"** (ngắn gọn) của SNARK — verify luôn nhanh, bất kể circuit phức tạp đến đâu.

  

---

  

## 8. Tamper Test (`verify-tampered.js`)

  

Project có bài test kiểm tra **tính soundness**:

  

### Tấn công 1: Nói dối về output

  

```js

// Dùng proof thật của a×b=15, nhưng claim c=99

const fakePub = ["99"];

await snarkjs.groth16.verify(vKey, fakePub, proof);

// → false ✓ (bị từ chối đúng đắn)

```

  

### Tấn công 2: Làm hỏng proof

  

```js

// Lật 1 bit trong pi_a

badProof.pi_a[0] = original.slice(0, -1) + "X";

await snarkjs.groth16.verify(vKey, pubSigs, badProof);

// → false ✓ (bị từ chối đúng đắn)

```

  

Cả hai đều bị từ chối → **Soundness được đảm bảo!**

  

---

  

## 9. Cấu trúc thư mục

  

```

zk-multiply/

│

├── index.js                  ← Entry point, chạy toàn bộ flow

├── verify-tampered.js        ← Demo tamper test

├── package.json

│

├── circuits/

│   ├── multiply.circom       ← SOURCE: mã nguồn circuit (đọc cái này!)

│   └── compiled/             ← OUTPUT của circom compiler

│       ├── multiply.r1cs     ← Hệ ràng buộc R1CS (binary)

│       ├── multiply.sym      ← Symbol table (debug)

│       └── multiply_js/

│           └── multiply.wasm ← Witness calculator (WebAssembly)

│

├── bin/

│   └── circom.exe            ← circom compiler (tự download)

│

└── build/                    ← OUTPUT của quá trình chạy

    ├── pot_final.ptau         ← Powers of Tau (Phase 1 output)

    ├── multiply_final.zkey   ← Proving key (Phase 2 output)

    ├── verification_key.json ← Verification key (chia sẻ công khai)

    ├── proof.json            ← Proof được tạo bởi Prover

    └── public.json           ← Public signals [c = 15]

```

  

---

  

## 10. Để học thêm

  

| Tài nguyên | Link |

|---|---|

| circom documentation | https://docs.circom.io/ |

| snarkjs GitHub | https://github.com/iden3/snarkjs |

| ZKP Explained (EN) | https://zkproof.org/2020/06/08/introduction-to-zk-snarks/ |

| Groth16 Paper | https://eprint.iacr.org/2016/260.pdf |

| ZK-learning.org | https://zk-learning.org/ |