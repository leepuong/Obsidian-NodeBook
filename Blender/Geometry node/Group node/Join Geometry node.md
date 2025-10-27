---
tags:
  - Blender
  - Geometry
---
kết hợp các hình học được tạo riêng biệt thành một hình học duy nhất. Nếu đầu vào hình học chứa các kiểu dữ liệu khác nhau, thì đầu ra cũng sẽ chứa các kiểu dữ liệu khác nhau.
![[image-9 1.png]]

## Materials
- khi đưa nhiều **mesh** vào **node**, mỗi mesh có **materials** khác nhau, **Blender** sẽ tự động gộp **material slots**, và **mesh** đầu ra sẽ chứa tất cả các **vật liệu từ mesh thành phần**. 
## Attributes
- Khi **gộp (merge) nhiều geometry** lại, Blender cũng phải gộp luôn **attributes** (thuộc tính) đi kèm mỗi geometry.
- Nếu các geometry đầu vào có cùng tên attribute nhưng **khác kiểu dữ liệu**, Blender sẽ **nâng cấp** attribute đó lên **kiểu dữ liệu phức tạp hơn** để đảm bảo giữ được thông tin.

Thứ bậc **"độ phức tạp"** **(simplified)**
- **Boolean** → đơn giản nhất (chỉ True/False).
- **Integer** → số nguyên.
- **Float** → số thực (linh hoạt hơn int).
- **Vector** → chứa nhiều số thực (ví dụ 3 thành phần).
- **Color** → cũng là một dạng vector RGBA.

==✒️Ghi chú==
- Node này không thể xứ lý đầu vào có nhiều hơn 1 [[Volume]].
- Vertex groups are preserved when realizing instances or joining geometries. If the domain and type propagation rules above result with the vertex domain and float type, then an attribute will be a vertex group on the output mesh.

==🔥Quan trọng==
	none

## Inputs
- Nhiều geometry.

## Properties
- none
## Outputs
- Geometry

## Get it
- [[Get node#Join Geometry node]]
