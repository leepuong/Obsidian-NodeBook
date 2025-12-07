



*slide1*
Xin chào thầy và các bạn, mình là Lê Xuân Phương StudentID BD00657, đại điện nhóm 3 lên đây để chia sẻ với mọi người một chủ đề:
chủ đề đó mang tên: **Ứng dụng của Lý thuyết nhóm trong đồ họa máy tính**

*Tatble of content*
1. giới thiệu
2. lý thuyết cơ bản của lý thuyết nhóm.
3. ứng dụng lý thuyết nhóm
4. lợi ích của việc áp dụng
5. thử thách và giới hạn.

phần trình bày này của chúng em gồm 5 phần như trên.
Phần đầu sẽ giới thiệu sơ về lý thuyết nhóm và tại sao nó liên quan đến ĐỒ họa máy tính.
đồng thời là 1 số lý thuyết cơ bản của lý thuyết nhóm.


*slide2*
đầu tiên **lý thuyết nhóm là gì** và **nó liên quan thế nào đến đồ họa máy tính**.

*slide3*
Lý thuyết nhóm là 1 nhánh của đại số trừu tượng, nghiên cứu về các phép toán và cấu trúc đối xứng.

*slide4*
còn tại sao nó liên quan đến Đồ họa máy tính, bởi lẽ Group theory cung cấp ngôn ngữ toán học chuẩn để mô tả các phép biển đổi hình học và đối xứng, những thứ mà xuất hiện gần như ở mọi bước trong dựng hình, mô phòng, animation.

*Slide5*
trước khi tiếp tục chủ đề chúng ta cần nắm 1 số lý thuyết cơ bản của lý thuyết nhóm.

*Slide6*
đầu tiên là group. group là 1 nhóm tập hợp G với 1 phép toán thảo mãn 4 tính chất sau:
....

*Slide7*
Tiếp theo là **Identity Element** nói rằng: trong 1 nhóm Luôn tồn tại một phần tử e sao cho: a . e = e . a = a. với mọi a thuộc G.

*slide8*
lý thuyết **Inverse Element**: nếu mỗi phần tử a thuộc G đều có 1 nghịc đảo a^-1 thỏa: a∗(a^−1)=(a^−1)∗a=e

**Slide0 return table of content**

Đó là các lý thuyết cơ bản nhất của group theory, chúng ta sẽ quay trở lại với việc ứng dụng group theory vào đồ họa máy tính như thế nào.
để gần gũi nhất thì mình sẽ cùng tìm hiểu qua câu hỏi 

*Slide9*
**làm thể nào để xoay vật thể 3d.**
	để mà nói ý, thì việc xoay 1 vật thể trong không gian 3d như xoay theo trục x, y hay z, quay kết hợp nhiều phép quay, quay liên tục mượt mà. 
	nếu không quản lý đúng, vật thể có thể bị biến dạng, lỗi gimbal lock, hoặc mất ổn định...

*Slide10*
Khi này, Lý thuyết nhóm cung cấp khuôn khổ toán học giúp:  
	Biểu diễn phép quay một cách có hệ thống.  
	Kết hợp nhiều phép quay dễ dàng.  
	Đảm bảo không làm thay đổi kích thước hay hình dạng vật thể.  
	Giữ được tính ổn định khi lặp lại phép quay nhiều lần.

	👉 TẤT CẢ các phép quay trong không gian 3D đều tạo thành một nhóm phép quay.

*Slide11*
