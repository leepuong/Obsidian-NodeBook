---
tags:
  - Blender
  - Geometry
---
Nút "**Subdivision Surface**" cho thêm các mặt mới vào hình học lưới bằng phương pháp phân chia nhỏ Catmull-Clark
![[image 9.png]]

## Inputs
- Mesh
	- Đầu vào hình học tiêu chuẩn
- Level
	- Mức độ phân chia để áp dụng cho hình học đầu vào
- [[Edge Crease]]
	- Điều khiển mức độ sắc của các cạnh
- [[Vertex Crease]]
	- Điều khiển lượng bề mặt phân hóa sẽ được co kéo về phía điểm đỉnh
- [[Limit Surface]]
	- Giới hạn mực độ phân chia ở các đỉnh đủ để tạo ra bề mặt mịn màn

## Properties
- **UV Smooth**: Quy định mức độ "giữ nguyên" các đặc điểm của lưới khi làm mượt UV
	- **None**: Không làm mượt gì cả. UV được giữ nguyên thô, chỉ unwrap theo seam
	- **Keep Corners**: Giữ cố định các **góc** (vertices ở các đỉnh sắc). Các cạnh khác có thể được làm mượt
	- **Keep Corners, Junctions**: Giữ cố định cả **góc** và **junctions** (điểm nơi nhiều cạnh giao nhau, giống “ngã tư” trong lưới). Những điểm này không bị kéo giãn khi smoothing UV
	- **Keep Corners, Junctions, Concave**: Ngoài góc và junctions, còn giữ thêm các **đỉnh lõm (concave vertices)** – những chỗ lõm vào (góc > 180°). Điều này giúp UV không bị bóp méo tại các vùng lõm phức tạp
	- **Keep Boundaries**: Giữ cố định các **cạnh biên (boundary edges)** – những cạnh nằm ở rìa UV island. UV ở bên trong vẫn có thể được làm mượt
	- **All**: Làm mượt toàn bộ UV, không giữ nguyên bất kỳ cạnh/góc nào. Điều này cho UV rất “mềm”, nhưng dễ gây méo hình nếu model có nhiều góc cứng
- **Boundary Smooth**: 
	- **All**: Làm mượt toàn bộ biên (boundary edges). Các cạnh ở rìa UV island đều được điều chỉnh cho “mượt” hơn, không giữ lại góc cố định. Điều này cho biên UV đẹp, mềm, nhưng có thể làm mất đi độ chính xác ở các góc.
	- **Keep Corners**: Chỉ làm mượt phần biên **trừ các góc**. Các góc (corner vertices) sẽ được giữ nguyên tại chỗ để tránh biến dạng, còn các đoạn cạnh giữa các góc thì có thể được làm mượt.

## Outputs
- Mesh
	- Đầu ra hình học tiêu chuẩn.

## Get it
- [[Get node#Subdivision Surface node]]
