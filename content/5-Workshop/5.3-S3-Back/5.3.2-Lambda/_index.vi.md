---
title : "Khởi tạo AWS Lambda"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.3.2.</b> "
---

#### Khởi tạo AWS Lambda (Worker)

AWS Lambda là dịch vụ điện toán không máy chủ (Serverless Computing) của Amazon Web Services (AWS), cho phép thực thi mã nguồn mà không cần quản lý hạ tầng máy chủ. Trong hệ thống Trang Đặt Vé Sự Kiện, AWS Lambda đảm nhiệm vai trò xử lý nghiệp vụ đặt vé sau khi các yêu cầu được gửi vào Amazon SQS.

Sau khi hoàn thành việc triển khai Amazon RDS PostgreSQL, bước tiếp theo là khởi tạo một Lambda Function để xử lý các yêu cầu đặt vé. Lambda sẽ được cấu hình cùng Virtual Private Cloud (VPC) với Amazon RDS nhằm đảm bảo có thể kết nối và thao tác trực tiếp với cơ sở dữ liệu.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console**, tìm kiếm dịch vụ **AWS Lambda** và chọn **Create function**.
- Chọn **Author from scratch** để tạo một Lambda Function mới.
- Đặt **Function name** là `flashsale-ticket-node`.
- Tại mục **Runtime**, chọn **Node.js 20.x**.
- Giữ nguyên **Architecture** là **x86_64**.

Tiếp theo, tiến hành cấu hình quyền truy cập cho Lambda:

- Trong mục **Permissions**, chọn **Change default execution role**.
- Giữ nguyên tùy chọn **Create a new role with basic Lambda permissions** để AWS tự động tạo IAM Role mặc định cho Lambda.
- IAM Role này ban đầu chỉ có quyền ghi nhật ký lên Amazon CloudWatch. Các quyền truy cập Amazon SQS, Amazon RDS và AWS Secrets Manager sẽ được bổ sung ở các bước cấu hình tiếp theo theo nguyên tắc **Least Privilege (Đặc quyền tối thiểu)**.


Ở phần **Advanced settings**, tiến hành cấu hình kết nối mạng như sau:

- **Enable VPC:** Bật kết nối VPC cho Lambda.
- **Virtual Private Cloud (VPC):** Chọn **Default VPC**.
- **Subnets:** Chọn tất cả các Subnet trong VPC.
- **Security Groups:** Chọn Security Group mặc định hoặc Security Group đã được tạo cho hệ thống.

Việc cấu hình VPC giúp AWS Lambda có thể truy cập Amazon RDS PostgreSQL, do cơ sở dữ liệu đã được thiết lập **Public access = No** và chỉ cho phép kết nối từ các tài nguyên nằm trong cùng mạng nội bộ.

Sau khi hoàn tất các thiết lập, nhấn **Create function** để tạo Lambda Function. Khi trạng thái của Function chuyển sang **Active**, Lambda đã sẵn sàng để được kết nối với Amazon SQS và thực hiện xử lý các yêu cầu đặt vé.

![lambda-vpc](/images/5-Workshop/5.3-S3-vpc/lambda.jpg)