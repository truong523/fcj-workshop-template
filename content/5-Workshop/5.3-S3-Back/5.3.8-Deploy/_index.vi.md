---
title : "Triển khai mã nguồn lên AWS Lambda"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b>5.3.8.</b> "
---

#### Triển khai mã nguồn lên AWS Lambda

Sau khi hoàn tất việc đóng gói mã nguồn thành tệp **deploy.zip**, bước tiếp theo là tải mã nguồn lên AWS Lambda để triển khai hàm xử lý nghiệp vụ đặt vé. AWS Lambda hỗ trợ triển khai trực tiếp từ tệp ZIP, giúp cập nhật mã nguồn nhanh chóng mà không cần cấu hình thêm máy chủ.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console** và mở dịch vụ **AWS Lambda**.
- Chọn Function **flashsale-ticket-worker** đã được tạo ở các bước trước.
- Chuyển sang tab **Code**.
- Nhấn **Upload from** và chọn **.zip file**.
- Chọn tệp **deploy.zip** đã được tạo từ thư mục dự án.
- Nhấn **Save** để bắt đầu quá trình tải và triển khai mã nguồn.


Sau khi quá trình tải lên hoàn tất, AWS Lambda sẽ tự động cập nhật phiên bản mã nguồn mới. Người triển khai có thể kiểm tra nội dung tệp **index.js** trực tiếp trên giao diện AWS Lambda để xác nhận việc triển khai đã thành công.

![lambda-code](/images/5-Workshop/5.3-S3-vpc/8.jpg)

Việc triển khai mã nguồn thành công là cơ sở để AWS Lambda có thể tiếp nhận các thông điệp từ Amazon SQS và thực hiện xử lý nghiệp vụ đặt vé theo kiến trúc Serverless đã được thiết kế.