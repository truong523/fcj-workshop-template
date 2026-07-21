---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b>5.</b> "
---

# Xây dựng Hệ thống Đặt Vé Sự Kiện Giới Hạn trên nền tảng AWS Serverless

#### Tổng quan

Trong workshop này, chúng ta sẽ xây dựng một **Hệ thống Đặt Vé Sự Kiện Giới Hạn (Flash Sale Ticket Booking System)** dựa trên kiến trúc **AWS Serverless Event-Driven**.

Hệ thống được thiết kế nhằm xử lý số lượng lớn yêu cầu đặt vé trong thời gian ngắn, đồng thời hạn chế **Race Condition** và **Overbooking**. Yêu cầu đặt vé từ người dùng sẽ được tiếp nhận thông qua **Amazon API Gateway**, đưa vào **Amazon SQS** để xếp hàng xử lý, sau đó **AWS Lambda** sẽ thực hiện nghiệp vụ đặt vé và cập nhật dữ liệu vào **Amazon RDS PostgreSQL**.

Bên cạnh đó, hệ thống sử dụng **AWS Secrets Manager** để bảo mật thông tin kết nối cơ sở dữ liệu, **Amazon SES** để gửi email xác nhận đặt vé và **Amazon CloudWatch** để giám sát hoạt động của toàn bộ hệ thống. Giao diện người dùng được xây dựng bằng HTML, CSS và JavaScript, sau đó triển khai trên **AWS Amplify**.

Thông qua workshop này, người học sẽ thực hành triển khai một hệ thống đặt vé hoàn chỉnh theo mô hình Serverless trên AWS, từ việc xây dựng cơ sở dữ liệu, triển khai Backend, Frontend cho đến đánh giá kết quả của hệ thống.

#### Nội dung

1. [Tổng quan hệ thống](5.1-Workshop-overview/)
2. [Chuẩn bị môi trường](5.2-Prerequisite/)
3. [Triển khai Backend Serverless](5.3-Backend-serverless/)
4. [Triển khai Frontend Website](5.4-Frontend/)
5. [Đánh giá](5.5-Evaluation/)