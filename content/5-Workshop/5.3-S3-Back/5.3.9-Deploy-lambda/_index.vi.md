---
title : "Tải mã nguồn lên AWS Lambda"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b>5.3.9.</b> "
---

#### Tải mã nguồn lên AWS Lambda

Sau khi hoàn tất việc chuẩn bị và đóng gói mã nguồn thành tệp **deploy.zip**, bước tiếp theo là tải gói triển khai lên **AWS Lambda**. AWS Lambda hỗ trợ triển khai trực tiếp từ tệp ZIP, giúp cập nhật mã nguồn nhanh chóng và thuận tiện mà không cần cấu hình máy chủ.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console** và mở dịch vụ **AWS Lambda**.
- Chọn Function **flashsale-ticket-worker** đã được tạo ở các bước trước.
- Chuyển sang tab **Code**.
- Nhấn **Upload from** và chọn **.zip file**.
- Chọn tệp **deploy.zip** đã được tạo từ thư mục dự án.
- Nhấn **Save** để bắt đầu quá trình tải và triển khai mã nguồn.


Sau khi quá trình tải lên hoàn tất, AWS Lambda sẽ tự động cập nhật phiên bản mã nguồn mới. Người triển khai có thể kiểm tra nội dung tệp **index.js** trực tiếp trên giao diện AWS Lambda để xác nhận việc triển khai đã thành công.

![lambda-code](/images/5-Workshop/5.3-S3-vpc/8.jpg)

Khi mã nguồn được triển khai thành công, AWS Lambda đã sẵn sàng tiếp nhận các thông điệp từ **Amazon SQS**, kết nối với **Amazon RDS PostgreSQL** và thực hiện quy trình xử lý đặt vé theo kiến trúc **Serverless Event-Driven** của hệ thống.