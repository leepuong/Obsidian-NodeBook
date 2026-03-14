






tìm đề tài


tìm theo chiều dọc:
- tìm công nghệ mới
- phát triển đề tài theo công nghệ đó.

1 hướng tìm đề tài khác

- tìm từ các cuộc tấn công phổ biến, ta biết được các cuộc tấn công này dùng phương thức nào, từ đây tôi có thể tìm các phương pháp đã tồn tại có thể chống lại phương thức này. 
	- vậy đầu tiên tôi cần tìm hiểu có các cuộc tấn công phổ biến nào đúng k?
		- đúng!
	- tôi có thể tìm bằng cách nào.
		- có thể dùng chatAI
	- tôi cần promtp như thế nào để có thể tìm đúng chủ đề này.
		- "hiện nay có những cuộc tấn công thuộc lĩnh vực cyber security nào phổ biến"
	- nhưng làm sao để tìm ra được các cuộc tấn công vừa có giải pháp vừa ít người chọn 


yêu cầu: 
	tạo file yêu cầu dự án
	


firts look
- dự án có 1 landing page.
	- ở landing page có ô nhập team code.
	- ở landing page có btn make a team.
		- [[#^ae2215]]
- dự án có 1 page sảnh chờ
	- có các slot thành viên.
		- [[#^36b0bc]]


##### Chức năng
chức năng tạo team
	Tạo code join team. 
	Add friend. [[#^329a16]] ^ae2215

chức năng add friend
	 ^329a16

##### Thành phần
	


##### Design
	giống sảnh chờ valorant ^36b0bc

#### Project Initiation
##### 1.1 xác định vấn đề 
- 1.1 tích hợp phương thức đăng nhập sử dụng tư duy zero knowledge
- 2.1 tạo web side cho phép người dùng tạo nhóm và lên chiến thuật valorant
	- chọn agent
	- tạo team
	- ...
- 2.2 đối tượng là các người chơi game V. admin quản lý website. (có 1 số role sử dụng trong thời gian phát triển: DatabaseController, UserController,...)
- **Problem Statement**
	- Hiện nay, game V là game bắn súng chiến thuật số 1 thế giới, không chỉ có những kỹ năng thuần aim, mà còn là những chiến thuật tấn công phòng thủ độc đáo với các bộ kỹ năng của các agent. Nhưng vấn đề thảo luận chiến thuật cũng chỉ thông qua lời nói trong game, nó rời rạc đẫn đến khó định hình và khó quản lý.
	- Do đó công cụ của chúng tôi sinh ra nhằm tạo ra không gian tăng hiệu xuất, tăng sức nắm bắt khi bàn chiến thuật với nhiều công cụ trực quan hóa.
##### 1.2 Xác định mục tiêu dự án



**Zero-Knowledge Proof**


$1-2^{-t}$



vì t là số lần nên là số nguyên
```math
t = 1000
1 - 2^-t =>
t = 10
1 - 2^-t =>
t = 3
1 - 2^-t =>
t = 2
1 - 2^-t =>
t = 1
1 - 2^-t =>
t = 0
1 - 2^-t =>
```



[[Zero-knowledge_proofs_for_set_membership_efficient,succinct,modular.pdf#page=1&selection=33,0,33,71&color=yellow|Received: 6 July 2022 / Revised: 1 March 2023 / Accepted: 3 May 2023 /]]




[[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=0,0,1,31&color=note|LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs, p.2]]
##### Abstract
- chúng tôi xây dựng các modul có thể kết hợp với nhau như việc lắp ghép lego.










# Giai đoạn 0 – Xác định mục tiêu

### ❓ Hệ thống cần chứng minh điều gì?
Ví dụ:
- Biết mật khẩu
- Là thành viên hợp lệ 
- Trên 18 tuổi 
- Sở hữu private key 

👉 **Chỉ chọn 1 điều kiện đơn giản trước.**  
Không xây hệ thống lớn ngay.

---

# Giai đoạn 1 – Hiểu và thử zero-knowledge cơ bản

### ❓ Zero-knowledge proof là gì ở mức thực hành? 
**Mục tiêu:** hiểu proof được tạo và verify như thế nào.

### Việc cần làm: 
1. Dùng một thư viện zk-SNARK đơn giản (chưa cần Lego)
2. Viết một circuit cực nhỏ:

Ví dụ: 
Tôi biết x sao cho x * x = 25 
3. Tạo proof 
4. Verify proof 

Nếu bạn chưa làm được bước này → chưa nên sang LegoSNARK.

---

# Giai đoạn 2 – Viết circuit dạng R1CS đơn giản

### ❓ Làm sao chuyển logic thành ràng buộc số học? 
**Mục tiêu:** hiểu constraint hoạt động ra sao.

### Việc cần làm: 
1. Viết một circuit kiểm tra: 

hash(password) = H

2. Triển khai SHA256 circuit (hoặc hash đơn giản hơn để test) 
3. Test: 

- Đúng password → proof hợp lệ 
- Sai password → proof fail 

---

# Giai đoạn 3 – Tách circuit thành module (bắt đầu tư duy Lego)

### ❓ Làm sao chia logic thành khối nhỏ? 
**Mục tiêu:** hiểu modularity. 
Ví dụ thay vì: 
Login + Age + Membership 
Tách thành: 
- Module 1: Password 
- Module 2: Age check 
- Module 3: Merkle membership 

### Việc cần làm: 
1. Build từng circuit riêng 
2. Test proof riêng từng module 
3. Đảm bảo mỗi module có proving/verifying key riêng 

---

# Giai đoạn 4 – Dùng LegoSNARK để ghép module

### ❓ Làm sao combine nhiều proof? 
**Mục tiêu:** hiểu cách LegoSNARK cho phép composition.

Việc cần làm: 
1. Tạo sub-circuit độc lập 
2. Generate CRS (trusted setup) cho từng module 
3. Compose thành main circuit 
4. Generate combined proof 

Ở đây bạn bắt đầu khai thác đúng điểm mạnh của LegoSNARK: 
- Tái sử dụng module 
- Không rebuild toàn bộ hệ thống 

---

# Giai đoạn 5 – Thiết kế luồng Authentication hoàn chỉnh

### ❓ Client và Server sẽ làm gì?

### Kiến trúc chuẩn:

## Client:

- Nhập password
    
- Generate proof local
    
- Gửi proof lên server
    

## Server:

- Nhận proof
    
- Verify proof
    
- Trả về token nếu hợp lệ
    

---

# Giai đoạn 6 – Xử lý bảo mật thực tế

### ❓ Làm sao tránh replay attack?

Cần:

- Nonce (số ngẫu nhiên mỗi lần login)
    
- Thêm nonce vào circuit
    
- Server kiểm tra nonce chưa dùng
    

---

### ❓ Làm sao lưu trữ an toàn?

Không lưu password.

Chỉ lưu:

- Public hash
    
- Hoặc commitment
    

---

# Giai đoạn 7 – Tối ưu hiệu năng

### ❓ Proof có chậm không?

Cần đo:

- Thời gian proving
    
- Thời gian verify
    
- Kích thước proof
    

Tối ưu bằng:

- Giảm constraint
    
- Tối ưu circuit hash
    
- Chọn elliptic curve phù hợp
    

---

# Giai đoạn 8 – Hoàn thiện hệ thống production

### Checklist hoàn chỉnh:

- Circuit modular
    
- Trusted setup an toàn
    
- Key management
    
- Logging verify
    
- Rate limiting
    
- API integration
    

---

# Lộ trình học theo thứ tự đúng

1. Hiểu R1CS
    
2. Viết circuit đơn giản
    
3. Tạo và verify proof
    
4. Tách module
    
5. Ghép module bằng LegoSNARK
    
6. Thiết kế client-server
    
7. Thêm bảo mật thực tế







#### 1.1.1. Rationale

- Trong kỷ nguyên chuyển đổi số toàn cầu, an ninh mạng (Cyber Security) không còn là một lựa chọn kỹ thuật mà đã trở thành ưu tiên chiến lược hàng đầu của mọi tổ chức. bởi các mối đe dọa như tấn công giả mạo (phishing), phần mềm độc hại (malware) và rò rỉ dữ liệu đang trở nên cấp bách hơn bao giờ hết, với ước tính khoảng 2.200 cuộc tấn công mạng xảy ra mỗi ngày trên toàn cầu.

**Sự bùng nổ của "Đại dịch" đánh cắp danh tính** Năm 2025 đánh dấu sự leo thang chưa từng có của các loại mã độc đánh cắp thông tin (infostealers). Theo các báo cáo nghiên cứu, đã có hơn 1,8 tỷ thông tin xác thực bị đánh cắp từ 5,8 triệu thiết bị chỉ trong vòng một năm, tương ứng với mức tăng 800% so với các giai đoạn trước đó. Các biến thể mã độc hiện đại như Lumma Stealer hay FleshStealer đã trở nên cực kỳ tinh vi, có khả năng vượt qua các giải pháp phòng thủ truyền thống (EDR) để trực tiếp khai thác kho lưu trữ mật khẩu trên trình duyệt và các tệp tin cookie phiên làm việc.

- 