---
title : "Cấu hình Amazone RDS"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.3.1</b> "
---

#### Khởi tạo Amazon RDS PostgreSQL

Amazon Relational Database Service (Amazon RDS) là dịch vụ cơ sở dữ liệu quan hệ được quản lý bởi Amazon Web Services (AWS). Trong hệ thống Trang Đặt Vé Sự Kiện, Amazon RDS sử dụng **PostgreSQL** để lưu trữ thông tin người dùng, dữ liệu vé và lịch sử đặt vé.

Amazon RDS được triển khai đầu tiên vì đây là dịch vụ có thời gian khởi tạo tương đối lâu, thường từ **10 đến 15 phút**. Việc tạo cơ sở dữ liệu trước giúp tận dụng thời gian chờ để tiếp tục cấu hình các dịch vụ khác như Amazon SQS, AWS Lambda và IAM, từ đó rút ngắn tổng thời gian triển khai hệ thống.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console**, tìm kiếm dịch vụ **Amazon RDS** và chọn **Create database**.
- Trong mục **Database creation method**, chọn **Standard Create**.
- Tại mục **Engine options**, chọn **PostgreSQL** làm hệ quản trị cơ sở dữ liệu.
- Trong mục **Templates**, chọn **Free Tier** để tiết kiệm chi phí trong quá trình triển khai và thử nghiệm.

Tiếp theo, tiến hành cấu hình các thông số cơ bản của cơ sở dữ liệu:

- **DB Instance Identifier:** Đặt tên cho cơ sở dữ liệu, ví dụ `flashsale-ticket-db`.
- **Master Username:** Thiết lập tài khoản quản trị cơ sở dữ liệu.
- **Master Password:** Thiết lập mật khẩu có độ bảo mật cao và lưu lại để sử dụng trong bước cấu hình AWS Secrets Manager.

![endpoint](/images/5-Workshop/5.3-S3-vpc/setting.png)

Ở phần **Connectivity**, cấu hình như sau:

- **Virtual Private Cloud (VPC):** Chọn **Default VPC**.
- **Public Access:** Chọn **No** để ngăn cơ sở dữ liệu truy cập trực tiếp từ Internet.
- **VPC Security Group:** Chọn **Create new** và đặt tên

Sau khi hoàn tất các thiết lập, nhấn **Create database** để Amazon RDS bắt đầu quá trình khởi tạo. Khi trạng thái của Database chuyển sang **Available**, cơ sở dữ liệu đã sẵn sàng để kết nối với các dịch vụ khác trong hệ thống.

![endpoint](/images/5-Workshop/5.3-S3-vpc/tlm.png)