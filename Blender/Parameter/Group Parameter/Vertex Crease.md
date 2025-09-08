---
tags:
  - Blender
  - Parameter
---
- Giống như [[Vertex Crease]], nhưng áp dụng **trực tiếp lên đỉnh (vertex)** thay vì cạnh.
- Được dùng khi bạn có một **cụm đỉnh giao nhau nhiều cạnh**, và muốn “giữ góc nhọn” tại đỉnh đó khi Subdivision Surface làm mượt.
- Giá trị cũng nằm trong khoảng **0.0 → 1.0**:
    - **0.0** = Subdivision làm tròn hoàn toàn.
        ![[image-5.png|338x282]]
    - **1.0** = giữ sắc mạnh nhất có thể.
        ![[image-4.png|335x285]]

> Nói cách khác: Edge Crease kiểm soát _dọc theo cạnh_, còn Vertex Crease kiểm soát _tại điểm giao giữa nhiều cạnh_.