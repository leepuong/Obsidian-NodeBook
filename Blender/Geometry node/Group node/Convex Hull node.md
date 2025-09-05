---
tags:
  - Blender
  - Geometry
---
Node **Convex Hull** trong Geometry Nodes của Blender dùng để tạo một **khối bao lồi** (convex shape) bao quanh toàn bộ tập hợp điểm/mesh được đưa vào, tức là hình dạng nhỏ nhất dạng lồi có thể bao trùm toàn bộ đối tượng.

![[Pasted image 20250830014517.png]]
Nhận Geometry và đẩy ra 1 Geometry khác những là phiên bản bị bọc lại

![[Pasted image 20250830015037.png|489x480]]
sau khi dùng [[Convex Hull node]] thì geometry đã được bọc lại
![[Pasted image 20250830015151.png|488x490]]

==✒️Ghi chú==
	Khi node được sử dụng trên một hình học có các thực thể, thuật toán sẽ thi hành một lần cho mỗi cá nhân thực thể, dẫn đến nhiều khung lưới bao lồi trong các hình học thực thể. Node "**Hiện Thực Hóa các Thực Thể**" có thể được sử dụng để lấy phần bao lồi của toàn bộ hình học.

==🔥Quan trọng==
	Các thể tích không được nút này hỗ trợ, và các thuộc tính không được tự động chuyển đến kết quả.

## Inputs
	- Geometry: Đầu vào hình học tiêu chuẩn.

## Properties
	- none

## Outputs
	- Convex Hull: Khung lưới bao bọc toàn bộ các điểm trong đầu vào.

## Get it
- [[Get node#Input node]]
