
```markmap
---
markmap:
  height: 621
  spacingVertical: 2
  spacingHorizontal: 50
  maxWidth: 500
  highlight: true
  coloring: depth
---
# Contents
## 0. Abstact
### **Quan điểm** ZKP đang trỗi dậy từ lý thuyết đến ứng dụng trong thực tế nhờ công nghệ phát triển mang lại nhiều giải pháp cho nhiều lĩnh vực.
### **Phân loại các hệ thống ZKP**
#### **SNARKs **(Succinct Non-Interactive Arguments of Knowledge)
#### **Commit-then-Prove ZKPs**
#### **MPC-in-the-Head**
#### **Sigma Protocols**
### **Hỗ trợ ra quyết định** bằng phương pháp luận **sơ đồ luồng (flowchart)** giúp xác định hệ thống ZKPs phù hợp với yêu cầu kỹ thuật và ứng dụng cụ thể.
### **Phân tích 3 trường hợp sử dụng chính**
#### **Outsourcing Computation** (Thuê ngoài tính toán)
#### **Digital Self-Sovereign Identity** (Định danh số tự chủ)
#### **ZKPs trong mạng máy tính** (networking)
### **Giải mã quy trình lựa chọn** làm sáng tỏ quá trình lựa chọn giúp hiểu rõ khi nào nên sử dụng ZKPs và khi nào tránh sử dụng nó.
## 1. Introduction
### **Sự tiến hóa của ZKPs** từ lý thuyết thuần túy thành những ứng dụng thực tế khả thi.
### **Mục tiêu**
#### 1. Hỗ trợ **tư duy phản biện** trong việc áp dụng ZKP cho cả nghiên cứu và thực tiễn công nghiệp
#### 2. **Thu hẹp khoảng cách** giữa lý thuyết và thực hành bằng cách làm rõ các cân nhắc và đánh đổi khi lựa chọn một hệ thống ZKP
### Giới thiệu **Phương pháp luận ra quyết định** để giúp người dùng chọn loại ZKP tối ưu hoặc **khuyến nghị không sử dụng** nếu không cần thiết cho kịch bản cụ thể.
### Nghiên cứu đi sâu vào phân tích ZKP trong 3 lĩnh vực
#### **ZKPs trong mạng máy tính** (networking)
#### **Digital Self-Sovereign Identity** (Định danh số tự chủ)
#### **Outsourcing Computation** (Thuê ngoài tính toán)
### **Tính cấp thiết và giải pháp thay thế**: mặc dù ZKP tốt những không bắt buộc trong mọi ngữ cảnh, trong 1 số ngữ cảnh, các giải pháp thay thế sẽ ít tốn kém hơn và có thể hiệu quả hơn.
### Làm rõ hiểu nhầm về thuật ngữ **Zero Knowledge**
## 2. On Argument Systems, SNARKs and Zero-Knowledge
### 2.0 **Thuật ngữ "Zero-Knowledge"**
#### Nhiều ứng dụng hiện đang lạm dùng thuật ngữ này.Thực tế, 1 số ứng dụng không thực sự cần tính bảo mật của **zero knowledge** mà chỉ dựa vào các tính chất khác như: **tính phi tương tác (non-interactivity)** hoặc **tính ngắn gọn (succinctness)** để phục vụ mục đích sử dụng.
### 2.1 **What is a Proof?**
```
