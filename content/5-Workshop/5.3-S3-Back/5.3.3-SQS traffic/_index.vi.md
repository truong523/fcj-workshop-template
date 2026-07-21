---
title : "Cấu hình Amazon SQS traffic"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3.3.</b> "
---

#### Cấu hình Amazon SQS

Amazon Simple Queue Service (Amazon SQS) là dịch vụ hàng đợi thông điệp được quản lý bởi Amazon Web Services (AWS). Trong hệ thống Trang Đặt Vé Sự Kiện, Amazon SQS được sử dụng để lưu trữ tạm thời các yêu cầu đặt vé trước khi được AWS Lambda xử lý.

Việc sử dụng Amazon SQS giúp tách biệt quá trình tiếp nhận yêu cầu từ người dùng và quá trình xử lý nghiệp vụ. Thay vì xử lý trực tiếp, tất cả các yêu cầu đặt vé sẽ được đưa vào hàng đợi và được AWS Lambda xử lý lần lượt. Cơ chế này giúp hệ thống có khả năng chịu tải cao, hạn chế tình trạng quá tải và đảm bảo tính ổn định khi có nhiều người dùng gửi yêu cầu đồng thời.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console**, tìm kiếm dịch vụ **Amazon SQS** và chọn **Simple Queue Service**.
- Kiểm tra Region đang sử dụng là **Asia Pacific (Singapore) – ap-southeast-1**.
- Chọn **Create queue** để tạo một hàng đợi mới.

Tiếp theo, tiến hành cấu hình các thông số của hàng đợi:

- **Type:** Chọn **Standard**.
- **Queue Name:** Đặt tên là `flashsale-booking-queue`.
- **Visibility Timeout:** Thiết lập **30 Seconds** để đảm bảo khi một AWS Lambda đang xử lý yêu cầu thì các Lambda khác sẽ không nhận cùng thông điệp đó.
- **Delivery Delay:** Giữ nguyên giá trị mặc định là **0 Seconds**.
- **Receive Message Wait Time:** Thiết lập **20 Seconds** nhằm kích hoạt cơ chế **Long Polling**, giúp giảm số lượng yêu cầu truy vấn đến Amazon SQS và tối ưu chi phí vận hành.
- **Message Retention Period:** Giữ nguyên giá trị mặc định là **4 Days**.


Sau khi hoàn tất các thiết lập, kéo xuống cuối trang và nhấn **Create queue** để tạo hàng đợi Amazon SQS.

Khi quá trình khởi tạo hoàn tất, hàng đợi **flashsale-booking-queue** sẽ sẵn sàng tiếp nhận các yêu cầu đặt vé từ Amazon API Gateway và chuyển đến AWS Lambda để xử lý theo cơ chế bất đồng bộ.

![sqs-created](/images/5-Workshop/5.3-S3-vpc/sqs.jpg)