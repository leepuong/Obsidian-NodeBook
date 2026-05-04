---

mindmap-plugin: basic

---

# LegoSNARK: Modular Design and Composition of Succinct Zero-Knowledge Proofs

## ## **ZKP**
- **Questions**
- **Contents**
	- Sub title
	- **Abstract**
		- Sub Contents
		- Key word
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=25,48,25,55&color=yellow|SNARKs]]
				- **Succinct Non-interactive Arguments of Knowledge.**
				**Succinct**: Bằng chứng nhỏ (vài trăm byte), xác minh nhanh.
				**Non-interactive**: Chỉ cần 1 lần gửi proof, không cần qua lại nhiều vòng.
				**Argument**: Độ an toàn dựa trên giả định tính toán (không phải chứng minh tuyệt đối).
				**of Knowledge**: Prover thực sự biết lời giải / witness
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=25,40,25,46&color=yellow|Gadet]]
				- mô tả như 1 công cụ nhỏ gọn có tác dụng đặc biệt là kết nối.
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=37,27,37,37&color=yellow|CP-SNARKs]]
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=43,6,43,13&color=yellow|lifting]]
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=58,52,58,67&color=yellow|Pedersen vector]]
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=57,32,57,47&color=yellow|Groth16 zkSNARK]]
		- Questions
	- **1 Introduction**
		- Sub Contents
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=175,0,175,10&color=red|Motivation]]
				- **zkSNARK đa năng** có tính biểu đạt cao nhưng lại hy sinh hiệu xuất để cố gắng trựu tượng hóa đặc điểm  toán học thành 1 dạng biểu hiện duy nhất.
				- **zkSNARK đa năng** đã bỏ lỡ sự đặc thù và không khai thác được từng sác thái của phép toán, ngược lại các giao thức chuyên biệt đạt hiệu quả vượt trội dựa vào các đặc thù riêng của phép toán.
			- Sub title
		- Key word
			- ZKPs
				- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=123,1,123,23&color=important|Zero-knowledge proofs]] được giới thiệu bởi Goldwasser, Micali và Rackoff
				- cho phép một người chứng minh thuyết phục một người xác minh về một khẳng định mà không tiết lộ thêm thông tin nào khác ngoài tính hợp lệ của khẳng định đó
			- [[Q0 LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=180,52,180,61&color=yellow|class NP]]
				- **Nondeterministic Polynomial time**
				- Dùng để phân loại các bài toán có thể không thể tìm thấy lời giải nhanh nhưng, kiểm tra đúng sai kết quả nhanh nếu có kết quả.
		- Questions