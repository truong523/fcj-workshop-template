---
title : "Lấy thông tin cấu hình từ AWS"
date : 2024-01-01
weight : 12
chapter : false
pre : " <b>5.3.12.</b> "
---

#### Lấy thông tin cấu hình từ AWS

Sau khi hoàn tất việc triển khai các dịch vụ trên AWS, bước tiếp theo là thu thập các thông tin cấu hình cần thiết để sử dụng trong mã nguồn ứng dụng. Hai thông tin quan trọng cần lấy là **RDS Endpoint** và **Secret Name** trong AWS Secrets Manager.

Các bước thực hiện như sau:

##### Lấy RDS Endpoint

- Truy cập **AWS Management Console** và mở dịch vụ **Amazon RDS**.
- Chọn **Databases** từ menu bên trái.
- Chọn cơ sở dữ liệu đã tạo, ví dụ: **flashsale-ticket-db**.
- Chuyển đến mục **Connectivity & security**.
- Sao chép giá trị tại trường **Endpoint**. Đây là địa chỉ dùng để kết nối ứng dụng với cơ sở dữ liệu PostgreSQL.


##### Lấy Secret Name

- Truy cập dịch vụ **AWS Secrets Manager**.
- Chọn Secret đã được tạo tự động khi khởi tạo Amazon RDS.
- Tại trang thông tin chi tiết, sao chép giá trị **Secret name**.

Thông tin này sẽ được AWS Lambda sử dụng để lấy tài khoản và mật khẩu cơ sở dữ liệu một cách an toàn mà không cần lưu trực tiếp trong mã nguồn.

![secret-name](/images/5-Workshop/5.3-S3-vpc/12.jpg)

Sau khi lấy được **RDS Endpoint** và **Secret Name**, lưu lại hai giá trị này để sử dụng trong bước cấu hình mã nguồn và thiết lập kết nối giữa AWS Lambda với Amazon RDS thông qua AWS Secrets Manager.