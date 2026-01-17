---
tags:
  - setup
  - Command
  - laptop
---



- **Thiết lập mức độ bảo mật khác nhau: PowerShell**
	- **Restricted**: *mực bảo mật mặc định của hệ thống, người dùng có thể nhập mcode nhưng không thể thực thi.*
	- **All Signed**: *mức này chỉ thực thi những phần được chỉ ra rõ ràng.*
	- **Remote Signed**: *các mã lệnh trên hệ thống được tạo ra tại máy chủ sẽ được thực thi còn các mã lệnh được tạo ra qua remote thì chỉ được phép chạy khi gán thuộc tính đầy đủ.*
	- **Unrestricted**: *không thiết lập chính sách bảo mật nào trên hệ thống.*
	- [ ] **VD ::** **Set-ExecutionPolicy UnRestricted**
- **Install WSL**
	- wsl --install
	- *install homebrew*
	- *install Ohmyzsh*
https://www.youtube.com/watch?v=jfv2eUHK8ow