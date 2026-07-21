---
title : "Mở AWS CloudShell"
date : 2024-01-01
weight : 14
chapter : false
pre : " <b>5.3.14.</b> "
---

#### Mở AWS CloudShell

Sau khi hoàn tất việc cấu hình AWS Lambda, bước tiếp theo là mở **AWS CloudShell** để thực hiện các thao tác dòng lệnh trực tiếp trên môi trường AWS. CloudShell là một terminal tích hợp sẵn trên AWS Management Console, cho phép người dùng sử dụng AWS CLI mà không cần cài đặt thêm phần mềm trên máy tính.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console**.
- Trên thanh điều hướng màu đen phía trên màn hình, tìm biểu tượng **CloudShell** (biểu tượng Terminal `>_`), nằm gần biểu tượng **Notifications**.
- Nhấn vào biểu tượng **CloudShell** để khởi động môi trường dòng lệnh.
- Chờ khoảng **20 đến 30 giây** để AWS khởi tạo phiên CloudShell.
- Sau khi hoàn tất, cửa sổ Terminal sẽ xuất hiện ở phía dưới màn hình và sẵn sàng tiếp nhận các lệnh AWS CLI.


Khi CloudShell khởi động thành công, hệ thống sẽ hiển thị cửa sổ dòng lệnh cùng thông tin tài khoản AWS đang sử dụng. Từ đây, người triển khai có thể thực hiện các lệnh quản trị, kiểm tra tài nguyên AWS hoặc cấu hình hệ thống mà không cần cài đặt AWS CLI trên máy tính cá nhân.


Việc sử dụng AWS CloudShell giúp đơn giản hóa quá trình quản trị hạ tầng trên AWS, đồng thời cung cấp môi trường làm việc an toàn với AWS CLI đã được cấu hình sẵn theo tài khoản hiện tại.