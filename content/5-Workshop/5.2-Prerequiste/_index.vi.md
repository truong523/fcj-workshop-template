---
title : "Kiến trúc "
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.2.</b> "
---


#### Kiến trúc tổng thể của hệ thống

Hệ thống được xây dựng theo mô hình **Serverless Event-Driven Architecture** trên nền tảng **Amazon Web Services (AWS)**. Kiến trúc này tách riêng quá trình tiếp nhận yêu cầu của người dùng và xử lý nghiệp vụ đặt vé, giúp hệ thống duy trì hiệu năng ổn định ngay cả khi có lượng lớn người dùng truy cập đồng thời.

Theo sơ đồ kiến trúc của hệ thống, luồng xử lý diễn ra như sau:

1. Người dùng truy cập Website đặt vé thông qua trình duyệt.
2. Toàn bộ lưu lượng truy cập được phân phối qua **Amazon CloudFront**, đồng thời **AWS WAF** kiểm tra và lọc các yêu cầu độc hại nhằm bảo vệ hệ thống khỏi các cuộc tấn công phổ biến trên nền Web.
3. Giao diện người dùng (Frontend) được triển khai trên **AWS Amplify Hosting**, giúp truy cập nhanh và ổn định.
4. Người dùng đăng nhập hoặc đăng ký tài khoản thông qua **Amazon Cognito**. Khi cần xác thực bổ sung, hệ thống sử dụng **AWS Lambda Custom Authorizer**.
5. Sau khi xác thực thành công, yêu cầu đặt vé được gửi đến **Amazon API Gateway**.
6. API Gateway chuyển toàn bộ yêu cầu vào **Amazon SQS Booking Queue** để xử lý bất đồng bộ, tránh tình trạng quá tải khi có nhiều người dùng gửi yêu cầu cùng lúc.
7. **AWS Lambda** tự động lấy từng yêu cầu từ Amazon SQS và thực hiện xử lý nghiệp vụ đặt vé.
8. Lambda kết nối với **Amazon RDS PostgreSQL**, thực hiện Transaction bằng cơ chế **SELECT ... FOR UPDATE** để khóa bản ghi, kiểm tra số lượng vé còn lại, cập nhật số lượng vé và lưu thông tin đặt vé nếu giao dịch thành công.
9. Trong quá trình hoạt động, toàn bộ nhật ký xử lý được ghi vào **Amazon CloudWatch**, đồng thời hệ thống gửi email xác nhận đặt vé thông qua **Amazon SES**.
10. Ngoài ra, các dịch vụ như **IAM**, **Secrets Manager**, **CloudTrail**, **AWS X-Ray**, **AWS Budgets** và **CloudFormation** hỗ trợ quản lý quyền truy cập, bảo mật dữ liệu, giám sát hoạt động, theo dõi hiệu năng và triển khai hạ tầng.

Kiến trúc này giúp hệ thống có khả năng mở rộng linh hoạt, chịu tải cao, giảm chi phí vận hành và đảm bảo tính ổn định khi triển khai các chương trình Flash Sale với số lượng người dùng lớn.


**Hình 5.1. Kiến trúc tổng thể hệ thống Trang Đặt Vé Sự Kiện Giới Hạn trên nền tảng AWS**

#### Các dịch vụ AWS sử dụng

Để xây dựng hệ thống Flash Sale Ticket, đề tài sử dụng nhiều dịch vụ của **Amazon Web Services (AWS)**. Mỗi dịch vụ đảm nhiệm một chức năng riêng trong toàn bộ quy trình xử lý của hệ thống.

| **Dịch vụ AWS** | **Vai trò trong hệ thống** |
|-----------------|----------------------------|
| **Amazon CloudFront** | Phân phối nội dung Website và tăng tốc truy cập cho người dùng. |
| **AWS WAF** | Bảo vệ hệ thống khỏi các cuộc tấn công Web như SQL Injection, XSS và DDoS cơ bản. |
| **AWS Amplify Hosting** | Triển khai và lưu trữ giao diện Website. |
| **Amazon Cognito** | Quản lý tài khoản và xác thực người dùng. |
| **Amazon API Gateway** | Tiếp nhận các yêu cầu đặt vé từ phía Client thông qua REST API. |
| **Amazon SQS** | Lưu trữ các yêu cầu đặt vé trong hàng đợi để xử lý tuần tự. |
| **AWS Lambda** | Thực hiện toàn bộ nghiệp vụ xử lý đặt vé theo mô hình Serverless. |
| **Amazon RDS PostgreSQL** | Lưu trữ thông tin người dùng, vé và lịch sử đặt vé. |
| **Amazon SES** | Gửi email xác nhận đặt vé thành công cho khách hàng. |
| **Amazon CloudWatch** | Theo dõi Log, giám sát và cảnh báo hoạt động của hệ thống. |
| **AWS X-Ray** | Theo dõi luồng xử lý và phân tích hiệu năng của ứng dụng. |
| **AWS IAM** | Quản lý quyền truy cập giữa các dịch vụ AWS. |
| **AWS Secrets Manager** | Lưu trữ an toàn thông tin kết nối cơ sở dữ liệu. |
| **AWS CloudTrail** | Ghi nhận lịch sử hoạt động của tài khoản AWS. |
| **AWS Budgets** | Theo dõi và cảnh báo chi phí sử dụng dịch vụ AWS. |
| **AWS CloudFormation** | Hỗ trợ triển khai và quản lý hạ tầng theo mô hình Infrastructure as Code (IaC). |