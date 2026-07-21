---
title : "Kiểm thử chịu tải hệ thống (Stress Testing)"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b>5.3.11.</b> "
---

#### Kiểm thử chịu tải hệ thống (Stress Testing)

Sau khi hoàn tất việc triển khai các thành phần của hệ thống Serverless, bước tiếp theo là kiểm tra khả năng chịu tải của hệ thống trong điều kiện có số lượng lớn người dùng truy cập đồng thời. Mục tiêu của bước này là đánh giá khả năng xử lý của Amazon SQS, AWS Lambda và cơ chế khóa dữ liệu (**FOR UPDATE**) trong PostgreSQL nhằm đảm bảo không xảy ra hiện tượng bán vượt số lượng vé (**Overbooking**).

Trong quá trình kiểm thử, sử dụng các công cụ tạo tải như **Apache JMeter**, **K6** hoặc một chương trình mô phỏng bằng **Node.js** hay **Python** để gửi đồng thời khoảng **1.000 yêu cầu đặt vé** vào hệ thống trong cùng một thời điểm.

Các bước thực hiện như sau:

- Chuẩn bị công cụ tạo tải (Apache JMeter, K6 hoặc chương trình Node.js/Python).
- Thiết lập số lượng yêu cầu gửi đồng thời, ví dụ **1.000 requests**.
- Gửi các yêu cầu đặt vé đến API Gateway hoặc đẩy trực tiếp vào Amazon SQS.
- Theo dõi quá trình xử lý của AWS Lambda thông qua **Amazon CloudWatch Logs**.
- Kiểm tra dữ liệu trong Amazon RDS sau khi quá trình kiểm thử kết thúc.


Trong cơ sở dữ liệu, giả sử bảng **tickets** được thiết lập với số lượng vé ban đầu (**stock**) là **10**. Sau khi hoàn tất quá trình kiểm thử, hệ thống được xem là hoạt động chính xác nếu đáp ứng các điều kiện sau:

- Số lượng vé còn lại (**stock**) bằng **0**.
- Chỉ có đúng **10 giao dịch đặt vé thành công** được ghi nhận trong bảng **bookings**.
- Các yêu cầu còn lại được từ chối do hết vé.
- Không xảy ra hiện tượng **Overbooking** hoặc ghi trùng dữ liệu.

Một ví dụ cụ thể: 



![stress-result](/images/5-Workshop/5.3-S3-vpc/11.2.jpg)

Việc kiểm thử chịu tải giúp đánh giá khả năng mở rộng của kiến trúc Serverless cũng như xác nhận rằng cơ chế xử lý đồng thời của Amazon SQS, AWS Lambda và PostgreSQL hoạt động chính xác trong điều kiện lưu lượng truy cập lớn.