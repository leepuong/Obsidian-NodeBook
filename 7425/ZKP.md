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
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=25,48,25,55&color=yellow|SNARKs]]
				- **Succinct Non-interactive Arguments of Knowledge.**
				**Succinct**: Bằng chứng nhỏ (vài trăm byte), xác minh nhanh.
				**Non-interactive**: Chỉ cần 1 lần gửi proof, không cần qua lại nhiều vòng.
				**Argument**: Độ an toàn dựa trên giả định tính toán (không phải chứng minh tuyệt đối).
				**of Knowledge**: Prover thực sự biết lời giải / witness
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=25,40,25,46&color=yellow|Gadet]]
				- mô tả như 1 công cụ nhỏ gọn có tác dụng đặc biệt là kết nối.
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=37,27,37,37&color=yellow|CP-SNARKs]]
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=43,6,43,13&color=yellow|lifting]]
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=58,52,58,67&color=yellow|Pedersen vector]]
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=57,32,57,47&color=yellow|Groth16 zkSNARK]]
		- Questions
	- **1 Introduction**
		- Sub Contents
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=175,0,175,10&color=red|Motivation]]
		- Key word
			- ZKPs
				- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=123,1,123,23&color=important|Zero-knowledge proofs]] được giới thiệu bởi Goldwasser, Micali và Rackoff
				- cho phép một người chứng minh thuyết phục một người xác minh về một khẳng định mà không tiết lộ thêm thông tin nào khác ngoài tính hợp lệ của khẳng định đó
			- [[LegoSNARK_Modular_Design_and_Composition_of_Succinct_Zero-Knowledge_Proofs.pdf#page=2&selection=180,52,180,61&color=yellow|class NP]]
				- **Nondeterministic Polynomial time**
				- Dùng để phân loại các bài toán có thể không thể tìm thấy lời giải nhanh nhưng, kiểm tra đúng sai kết quả nhanh nếu có kết quả.
		- Questions