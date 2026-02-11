






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












0. Abstact
	1. 