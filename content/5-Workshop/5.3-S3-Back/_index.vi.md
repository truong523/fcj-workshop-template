---
title : "Backend Serverless"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b>5.3.</b> "
---
#### Tổng quan

Trong phần này, bạn sẽ triển khai **Backend Serverless** cho hệ thống Trang Đặt Vé Sự Kiện trên nền tảng **Amazon Web Services (AWS)**. Mô hình Serverless giúp hệ thống xử lý yêu cầu đặt vé mà không cần quản lý máy chủ, đồng thời có khả năng tự động mở rộng khi số lượng người dùng tăng cao.

Backend của hệ thống được xây dựng dựa trên các dịch vụ cốt lõi của AWS như:

- **AWS Lambda**: Thực hiện xử lý toàn bộ nghiệp vụ đặt vé theo mô hình Serverless.
- **Amazon SQS**: Tiếp nhận và lưu trữ các yêu cầu đặt vé trong hàng đợi, giúp xử lý tuần tự và tránh quá tải khi có nhiều người dùng truy cập cùng lúc.
- **AWS IAM**: Quản lý quyền truy cập giữa các dịch vụ AWS theo nguyên tắc **Least Privilege** nhằm tăng cường bảo mật.
- **AWS Secrets Manager**: Lưu trữ an toàn thông tin kết nối cơ sở dữ liệu, tránh lưu trực tiếp mật khẩu trong mã nguồn.
- **Amazon RDS PostgreSQL**: Lưu trữ dữ liệu người dùng, thông tin vé và lịch sử đặt vé.
- **Amazon CloudWatch**: Theo dõi nhật ký (Logs) và giám sát quá trình hoạt động của hệ thống.

Trong chương này, bạn sẽ lần lượt thực hiện các bước tạo AWS Lambda, cấu hình Amazon SQS, phân quyền IAM, lưu trữ thông tin kết nối bằng AWS Secrets Manager và thiết lập Trigger giữa Amazon SQS với AWS Lambda để xây dựng hoàn chỉnh Backend Serverless cho hệ thống.

