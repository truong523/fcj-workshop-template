---
title: "Đánh giá"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b>5.5.</b> "
---


## Kết quả đạt được

Sau khi hoàn thành workshop, hệ thống đã triển khai thành công mô hình **AWS Serverless Event-Driven** cho bài toán đặt vé Flash Sale.

Các chức năng đã hoàn thành gồm:

- Xây dựng cơ sở dữ liệu **Amazon RDS PostgreSQL** để lưu trữ thông tin vé và người dùng.
- Triển khai **AWS Lambda** xử lý nghiệp vụ đặt vé.
- Sử dụng **Amazon SQS** làm hàng đợi giúp xử lý tuần tự các yêu cầu đặt vé.
- Triển khai **Amazon API Gateway** tiếp nhận yêu cầu từ Website.
- Kết nối **AWS Secrets Manager** để quản lý thông tin kết nối cơ sở dữ liệu.
- Gửi Email xác nhận đặt vé thành công bằng **Amazon SES**.
- Theo dõi log và quá trình xử lý bằng **Amazon CloudWatch**.
- Xây dựng giao diện Website và triển khai bằng **AWS Amplify**.
- Kiểm thử API bằng Postman và thực hiện Stress Test bằng AWS CloudShell.

---

## Ưu điểm

Hệ thống mang lại nhiều lợi ích so với mô hình xử lý truyền thống:

- Kiến trúc Serverless giúp không cần quản lý máy chủ.
- Tự động mở rộng khi số lượng người dùng tăng.
- Amazon SQS giúp giảm tải hệ thống khi có nhiều yêu cầu đồng thời.
- AWS Lambda chỉ được kích hoạt khi có yêu cầu nên tiết kiệm chi phí.
- PostgreSQL Transaction kết hợp `SELECT ... FOR UPDATE` giúp tránh tình trạng bán vượt số lượng vé (Overbooking).
- Amazon SES gửi Email xác nhận tự động sau khi đặt vé thành công.
- CloudWatch hỗ trợ theo dõi log và xử lý lỗi nhanh chóng.

---

## Hạn chế

Mặc dù hệ thống đã hoạt động ổn định nhưng vẫn còn một số hạn chế:

- Chưa tích hợp chức năng thanh toán trực tuyến.
- Chưa có cơ chế xác thực người dùng bằng Amazon Cognito.
- Chưa hỗ trợ Dashboard thống kê doanh thu và số lượng vé theo thời gian thực.
- Giao diện Website mới ở mức cơ bản và chưa tối ưu cho thiết bị di động.

---

## Hướng phát triển

Trong thời gian tới, hệ thống có thể được mở rộng với các chức năng sau:

- Triển khai toàn bộ hạ tầng bằng **AWS CloudFormation**, **AWS SAM** hoặc **Terraform** để tự động hóa quá trình triển khai.
- Tích hợp **Amazon Cognito** để quản lý người dùng và phân quyền.
- Bổ sung chức năng thanh toán trực tuyến thông qua các cổng thanh toán.
- Xây dựng Dashboard thống kê bằng Amazon QuickSight.
- Tối ưu hiệu năng bằng Amazon CloudFront và AWS WAF.
- Hỗ trợ nhiều sự kiện và nhiều loại vé hơn trong cùng một hệ thống.

---

## Mã nguồn

Toàn bộ mã nguồn và video demo của dự án được lưu trữ trên Google Drive:

**Google Drive link:** https://drive.google.com/drive/folders/1n_aHVtlblb3QDL-7qWoXmRGKMcIJziHT
