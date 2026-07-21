---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b>4.1.</b> "
---

# Báo cáo event Workshop "13-6 GenAI-powered App-DB Modernization"

## Mục đích của sự kiện

Workshop được tổ chức nhằm chia sẻ các phương pháp thiết kế và hiện đại hóa ứng dụng trên nền tảng AWS. Nội dung tập trung vào kiến trúc Serverless, Event-Driven Architecture và các dịch vụ AWS hỗ trợ xây dựng hệ thống có khả năng mở rộng, hiệu năng cao và dễ bảo trì.

---

## Nội dung nổi bật

### Kiến trúc Event-Driven

Một trong những nội dung quan trọng của workshop là giới thiệu kiến trúc **Event-Driven Architecture (EDA)**.

Kiến trúc này giúp các thành phần trong hệ thống giao tiếp thông qua sự kiện thay vì gọi trực tiếp lẫn nhau, mang lại nhiều lợi ích như:

- Giảm sự phụ thuộc giữa các thành phần.
- Tăng khả năng mở rộng hệ thống.
- Dễ dàng xử lý lượng lớn yêu cầu đồng thời.
- Nâng cao khả năng chịu lỗi.

Workshop cũng giới thiệu các mô hình truyền thông phổ biến:

- Publish/Subscribe
- Point-to-Point Messaging
- Event Streaming

---

### AWS Serverless

Workshop giới thiệu quá trình phát triển từ hạ tầng truyền thống sang Serverless:

- Amazon EC2
- Amazon ECS
- AWS Fargate
- AWS Lambda

AWS Lambda được đánh giá là phù hợp với các hệ thống có lưu lượng truy cập thay đổi liên tục nhờ:

- Không cần quản lý máy chủ.
- Tự động mở rộng.
- Chỉ tính phí khi có yêu cầu xử lý.
- Dễ tích hợp với các dịch vụ AWS khác.

---

### Thiết kế Microservices

Workshop chia sẻ phương pháp phân tách hệ thống thành các dịch vụ nhỏ theo Domain-Driven Design (DDD).

Các thành phần được tổ chức theo từng nghiệp vụ riêng biệt giúp:

- Dễ phát triển.
- Dễ bảo trì.
- Dễ mở rộng.
- Giảm ảnh hưởng khi cập nhật từng chức năng.

---

## Kiến thức học được

Sau khi tham gia workshop, tôi học được:

- Hiểu cách xây dựng hệ thống theo kiến trúc Event-Driven.
- Hiểu lợi ích của AWS Lambda trong mô hình Serverless.
- Biết cách sử dụng hàng đợi (Message Queue) để xử lý bất đồng bộ.
- Hiểu cách thiết kế hệ thống theo Microservices và Domain-Driven Design.
- Nắm được tư duy lựa chọn dịch vụ AWS phù hợp cho từng bài toán.

---

## Ứng dụng vào đề tài

Các kiến thức từ workshop được áp dụng trực tiếp vào đề tài **Hệ thống Đặt Vé Sự Kiện Giới Hạn trên nền tảng AWS Serverless**.

Cụ thể:

- Sử dụng **Amazon API Gateway** để tiếp nhận yêu cầu đặt vé.
- Sử dụng **Amazon SQS** làm hàng đợi xử lý yêu cầu theo mô hình Event-Driven.
- Sử dụng **AWS Lambda** để xử lý nghiệp vụ đặt vé.
- Sử dụng **Amazon RDS PostgreSQL** để lưu trữ dữ liệu và ngăn chặn tình trạng bán vượt số lượng vé bằng Transaction và `SELECT ... FOR UPDATE`.
- Theo dõi toàn bộ hệ thống bằng **Amazon CloudWatch**.

Việc áp dụng kiến trúc Event-Driven giúp hệ thống xử lý ổn định khi có nhiều người dùng truy cập đồng thời trong các chương trình Flash Sale.

---

## Bài học rút ra

Workshop giúp tôi hiểu rõ hơn về:

- Kiến trúc Event-Driven trên AWS.
- Mô hình Serverless và khả năng tự động mở rộng.
- Vai trò của Message Queue trong xử lý bất đồng bộ.
- Cách thiết kế hệ thống hiện đại có khả năng chịu tải cao.

Những kiến thức này là nền tảng quan trọng để xây dựng hệ thống đặt vé Flash Sale theo kiến trúc AWS Serverless trong đồ án.

