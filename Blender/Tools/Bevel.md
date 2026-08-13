# Bevel

> **Phím tắt:** `Ctrl + B` (Edge/Face Bevel) · `Ctrl + Shift + B` (Vertex Bevel)  
> **Chế độ:** Edit Mode  
> **Menu:** Mesh → Edge → Bevel Edges

---

## Bevel là gì?

**Bevel** là công cụ vát cạnh (edge) hoặc đỉnh (vertex) của mesh, tạo ra các cạnh bo tròn hoặc chamfer giữa hai mặt. Trong thực tế, không có vật thể nào có cạnh hoàn toàn sắc 100% — Bevel giúp model trông thực tế hơn và phản chiếu ánh sáng đúng hơn.

---

## Cách sử dụng cơ bản

### Edge Bevel

1. Vào **Edit Mode** (`Tab`)
2. Chọn một hoặc nhiều **Edge** (`2` để vào Edge Select mode)
3. Nhấn `Ctrl + B`
4. **Di chuột** ra ngoài để điều chỉnh độ rộng (width)
5. **Cuộn scroll wheel** để tăng/giảm số **segment**
6. Click chuột trái hoặc `Enter` để xác nhận

### Vertex Bevel

1. Chọn một hoặc nhiều **Vertex** (`1` để vào Vertex Select mode)
2. Nhấn `Ctrl + Shift + B`
3. Di chuột và scroll để điều chỉnh

---

## Operator Panel (F9 / góc dưới trái)

Sau khi thực hiện Bevel, mở **Last Operator Panel** (`F9`) để chỉnh lại các thông số:

| Thông số | Mô tả |
|---|---|
| **Width** | Độ rộng của bevel (đơn vị: Blender units hoặc %) |
| **Width Type** | Cách tính width: `Offset`, `Width`, `Depth`, `Percent`, `Absolute` |
| **Segments** | Số đoạn chia — càng nhiều càng tròn, mặc định là `1` (chamfer) |
| **Shape** | Độ cong của profile: `0` = lõm, `0.5` = thẳng, `1` = lồi |
| **Material Index** | Gán material riêng cho face bevel mới tạo |
| **Harden Normals** | Giữ normals của face gốc, tránh bóng bị méo |
| **Clamp Overlap** | Ngăn các bevel chồng lên nhau khi edge gần nhau |
| **Loop Slide** | Trượt loop dọc theo face thay vì khoảng cách cố định |
| **Mark Seam** | Tự động đánh dấu seam trên edge mới |
| **Mark Sharp** | Tự động đánh dấu sharp edge |
| **Miter Outer** | Cách xử lý góc ngoài (Sharp / Patch / Arc) |
| **Miter Inner** | Cách xử lý góc trong (Sharp / Arc) |
| **Spread** | Độ lan rộng của miter arc |
| **Vmesh Method** | Cách tạo face tại vertex giao nhau (Grid Fill / Cutoff) |
| **Face Strength Mode** | Gán face strength cho auto smooth |
| **Profile Type** | `Superellipse` (mặc định) hoặc `Custom` (vẽ curve tùy ý) |

---

## Segments & Shape

```
Segments = 1          Segments = 3          Segments = 8
(chamfer thẳng)       (bo nhẹ)              (gần tròn)

    /                   _                    ╭
   /                  _/                   ╭
  /                 _/                   ╭
```

- **Shape = 0.5** → đường thẳng (mặc định)
- **Shape > 0.5** → profile lồi ra ngoài (convex)
- **Shape < 0.5** → profile lõm vào trong (concave)

---

## Workflow thực tế

### Bo cạnh để bắt sáng đẹp hơn

Một kỹ thuật phổ biến trong hard-surface modeling:

1. Model xong shape cơ bản
2. Chọn tất cả edge cần bo (`Alt + Click` để chọn loop)
3. `Ctrl + B` → width nhỏ (~0.01–0.05) → segments = 2–3
4. Kết hợp với **Shade Smooth** + **Auto Smooth** để surface mượt

### Kết hợp với Bevel Weight

1. Chọn edge → `Ctrl + B` muốn kiểm soát riêng
2. Vào **Item Panel** (`N`) → Edge → **Bevel Weight** = 1.0
3. Thêm **Bevel Modifier** → bật **Limit Method: Weight**
4. Có thể chỉnh width không destructive từ modifier

---

## Bevel Modifier (non-destructive)

Thay vì dùng `Ctrl + B` trực tiếp (destructive), có thể dùng **Modifier**:

**Properties → Modifier → Add → Generate → Bevel**

Ưu điểm:
- Chỉnh sửa lại bất cứ lúc nào
- Kết hợp với **Bevel Weight** để kiểm soát từng edge
- Không phá hủy topology gốc

---

## Phím tắt trong khi thao tác Bevel

| Phím | Chức năng |
|---|---|
| `Scroll Up/Down` | Tăng / giảm số segment |
| `A` | Toggle giữa Even / UnEven |
| `C` | Toggle Clamp Overlap |
| `P` | Chỉnh Profile (Shape) trực tiếp |
| `S` | Chỉnh Spread |
| `V` | Chuyển sang Vertex Bevel |
| `M` | Chọn Miter type |
| `Esc` / `Right Click` | Hủy thao tác |

---

## Lưu ý & Tips

> [!tip] Tránh geometry xấu
> Khi bevel trên nhiều edge gặp nhau tại một vertex, dễ sinh ra **N-gon** hoặc **overlapping face**. Bật **Clamp Overlap** hoặc dùng **Miter** để xử lý.

> [!warning] Destructive vs Non-destructive
> `Ctrl + B` trong Edit Mode là **destructive** — thay đổi topology trực tiếp. Nếu muốn linh hoạt, dùng **Bevel Modifier** thay thế.

> [!note] Bevel + Subdivision Surface
> Khi dùng cùng **Subdivision Surface Modifier**, chỉ cần bevel nhỏ (1–2 segment) tại các hard edge để "giữ" hình dạng — SubD sẽ tự làm mượt phần còn lại.

---

## Liên quan

- [[Edit Mode]]
- [[Loop Cut]]
- [[Subdivision Surface Modifier]]
- [[Hard Surface Modeling]]
- [[Shade Smooth & Auto Smooth]]
- [[Bevel Weight]]
- [[Normals]]

---

*Tags: #blender #modeling #edit-mode #hard-surface #tool*
