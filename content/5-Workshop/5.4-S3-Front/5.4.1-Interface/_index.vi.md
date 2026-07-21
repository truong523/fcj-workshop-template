---
title : "Giao diện trang chủ và đặt vé"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.4.1.</b> "
---

#### Giao diện người dùng (Frontend)

Sau khi hoàn thành phần Backend trên AWS, hệ thống được xây dựng thêm giao diện Web để người dùng có thể xem danh sách sự kiện và thực hiện đặt vé trực tuyến. Giao diện được phát triển bằng HTML, CSS và JavaScript với phong cách hiện đại, tối ưu cho trải nghiệm người dùng.

##### 1. Trang chủ

Trang chủ hiển thị danh sách các sự kiện nổi bật cùng các thông tin cơ bản như:

- Tên sự kiện.
- Thời gian tổ chức.
- Địa điểm diễn ra.
- Giá vé.
- Nút **MUA VÉ** để chuyển sang trang đặt vé.

![home](/images/5-Workshop/5.4-S3-onprem/page1.jpg)

Người dùng có thể lựa chọn sự kiện mong muốn và nhấn **MUA VÉ** để bắt đầu quá trình đặt vé.

---

##### 2. Trang đặt vé

Sau khi chọn sự kiện, hệ thống chuyển sang giao diện đặt vé.

Người dùng cần nhập đầy đủ các thông tin:

- Chọn loại vé (Vé Thường hoặc Vé VIP).
- Họ và tên.
- Địa chỉ Email.
- Số điện thoại.

Sau khi hoàn tất, nhấn nút **MUA VÉ NGAY** để gửi yêu cầu đến hệ thống.

![booking](/images/5-Workshop/5.4-S3-onprem/page2.jpg)

Khi người dùng gửi biểu mẫu, trình duyệt sẽ gọi REST API của Amazon API Gateway. API Gateway tiếp nhận yêu cầu và chuyển thông điệp vào Amazon SQS để AWS Lambda xử lý theo kiến trúc Serverless, giúp hệ thống vẫn hoạt động ổn định khi có nhiều người cùng đặt vé.