---
title : "Xác nhận đặt vé qua Email"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.4.2.</b> "
---

#### Gửi Email xác nhận đặt vé

Sau khi AWS Lambda xử lý thành công yêu cầu đặt vé, hệ thống sẽ tự động gửi Email xác nhận đến địa chỉ mà người dùng đã đăng ký.

Email được gửi thông qua Amazon Simple Email Service (Amazon SES), bao gồm các thông tin:

- Loại vé đã đặt.
- Vị trí ghế ngồi.
- Số điện thoại liên hệ.
- Nội dung xác nhận đặt vé thành công.

![email](/images/5-Workshop/5.4-S3-Front/email.png)

Việc gửi Email xác nhận giúp người dùng kiểm tra lại thông tin đặt vé và sử dụng Email làm minh chứng khi tham gia sự kiện. Đây cũng là bước hoàn thiện quy trình xử lý đặt vé của hệ thống từ giao diện người dùng đến Backend trên nền tảng AWS.