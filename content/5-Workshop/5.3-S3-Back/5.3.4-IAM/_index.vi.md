---
title : "Cấu hình IAM"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.3.4.</b> "
---

#### Cấu hình IAM cho AWS Lambda

AWS Identity and Access Management (IAM) là dịch vụ quản lý danh tính và quyền truy cập của Amazon Web Services (AWS). Trong hệ thống Trang Đặt Vé Sự Kiện, IAM được sử dụng để cấp quyền cho AWS Lambda truy cập các dịch vụ cần thiết như Amazon SQS, Amazon RDS và AWS Secrets Manager.

Sau khi khởi tạo AWS Lambda, hệ thống cần cấp thêm quyền để Lambda có thể đọc và xử lý các thông điệp từ Amazon SQS. Việc phân quyền được thực hiện theo nguyên tắc **Least Privilege (Đặc quyền tối thiểu)**, chỉ cấp những quyền cần thiết nhằm tăng cường tính bảo mật cho hệ thống.

Các bước thực hiện như sau:

- Truy cập **AWS Lambda** và chọn Function **flashsale-ticket-node**.
- Chọn tab **Configuration**.
- Trong menu bên trái, chọn **Permissions**.
- Tại mục **Execution role**, nhấn vào đường dẫn của **IAM Role** được AWS tự động tạo cho Lambda.

Tiếp theo, tiến hành gán quyền cho IAM Role:

- Chọn **Add permissions**.
- Chọn **Attach policies**.
- Tìm kiếm chính sách **AWSLambdaSQSQueueExecutionRole**.
- Đánh dấu chọn chính sách vừa tìm được.
- Nhấn **Add permissions** để hoàn tất việc gán quyền.


Chính sách **AWSLambdaSQSQueueExecutionRole** cho phép AWS Lambda thực hiện các thao tác cần thiết trên Amazon SQS như nhận thông điệp, xóa thông điệp sau khi xử lý thành công và ghi nhật ký hoạt động lên Amazon CloudWatch.

Sau khi hoàn tất cấu hình, IAM Role của AWS Lambda đã được cấp quyền truy cập Amazon SQS và sẵn sàng cho bước cấu hình kết nối giữa Amazon SQS và AWS Lambda trong các phần tiếp theo.

![iam-role](/images/5-Workshop/5.3-S3-vpc/iam.jpg)