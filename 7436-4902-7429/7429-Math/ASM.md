---
tags:
  - Math-7429
---



##### **Tóm tắt ASM**
- 

P1
- [ ] giới thiệu về **giới thiệu về các phép toán tập hợp đại số**
- [ ] giải thích và ảnh các phép toán phổ biến như
	- [ ] $A \cap B$
	- [ ] $A \cup B$
	- [ ] $A - B$
	- [ ] $\overline{A}$ or $A'$
- [ ] giải các bài toán theo Student ID
	- [ ] lap1.1: Inclusion–Exclusion Principle for Two Sets
	số phần tử của A là $\overline{9b}$, B là $\overline{2a}$ và A $\cap$ B là $a+b$ vậy khi ID của tôi là BD00657 thì $a>b$ thì $a = 7, b = 6$
	$=>$  A có số phần tử là $97$ và B có số phần tử là $26$ 
	$=>$  A $\cap$ B có số phần từ là $a+b = 7 +6 = 13$ 
	Ta có thể dùng sơ đồ ven để trực quan chứng mình và tìm ra số phân tử của A $\cup$ B 
	A $\cup$ B được tìm bằng cách lấy A $\cap$ B trừ đi A tổng B
	ta có công thứ sau
	$$A \cup B = A + B - A \cap B$$

	![[7436-4902-7429/7429-Math/display.md#^area=UDfRHUUf0S5JL4xRsnbMn|lap.1]]
	- [ ] lap1.2
	giả sử $|A - B| = \overline{3a}$, $|A \cup B|=\overline{11b}$, $|A \cap B|=\overline{1a}$, xác định $|B|$
	với ID của tôi là BD00657 thì  $|A - B| = 37$, $|A \cup B|=116$, $|A \cap B|=17$
	Ta biết rằng: $|A|,|B| \in |A \cup B|$
	và 	$|A - B| + |B| = |A \cup B|$
	Nên $37 - |B| = 116$
	$\to |B| = 79$

	- [ ] lap1.3: Inclusion–Exclusion Principle for Three Sets
	![[7436-4902-7429/7429-Math/display.md#^area=XIdNDC03SugBUzSeK7Voh|lap.3]]
P2
- [ ] nếu **lý thuyết cái túi {| |}**, ứng dụng
- [ ] nếu **thừa số nguyên tố** và **ứng dụng** *????*
- [ ] giải các bài toán theo Student ID
	- [ ] Lap2.1
	ID của tôi là BD000657 và a > b nên số thứ nhất $\overline{1a2}$ chuyển thành 172
	số thứ 2 $\overline{2b0}$ chuyển thành 260.
		*phân tích số 172 và 260 thành tích các thừa số nguyên tố*
		chia số 172, 260 dần cho các số nguyên tố, cho đến khi kết quả bằng 1
		*Liệt kê “bag of prime factors”*
		a) 172 = 2 * 2 * 43
		$\to$ {|2, 2, 43|} = {|2:2, 43:1|}
		b) 260 = 2 * 2 * 5 * 13
		$\to$ {|2, 2, 5, 13|} = {|2:2, 5:1, 13:1|}
		1. **Tìm số lượng của mỗi túi**
			1. a) $|A| = \{ |2:2, 43:1| \} = 2 + 1 = 3$
			2. b) $|B| = \{ |2:2, 5:1, 13:1| \} = 2 + 1 + 1 = 4$
		2. **Giao của 2 túi trên**
			1. $A \cup B = \{ |2:2, 5:1, 13:1, 43:1| \}$
		3. **Hợp của 2 túi trên**
			1. $A \cap B = \{ |2:2| \}$
		4. **Hiệu của 2 túi trên**
			1. a)  $A -B = \{|43:1|\}$
			2. b)  $B - A = \{|5:1, 13:1|\}$
		


