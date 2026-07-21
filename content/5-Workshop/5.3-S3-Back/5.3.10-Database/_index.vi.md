---
title : "Kiểm tra luồng xử lý từ Amazon SQS"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b>5.3.10.</b> "
---

#### Kiểm tra luồng xử lý từ Amazon SQS

Sau khi hoàn tất việc cấu hình Amazon SQS, AWS Lambda và các quyền IAM cần thiết, bước tiếp theo là kiểm tra toàn bộ luồng xử lý của hệ thống. Mục tiêu của bước này là xác nhận rằng khi một thông điệp được gửi vào hàng đợi Amazon SQS, AWS Lambda sẽ tự động được kích hoạt và thực hiện xử lý nghiệp vụ đặt vé.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console** và mở dịch vụ **Amazon SQS**.
- Chọn hàng đợi **flashsale-booking-queue** đã được tạo ở các bước trước.
- Nhấn **Send and receive messages**.
- Tại ô **Message body**, nhập nội dung thông điệp theo định dạng JSON:

```json
{
  "ticketId": 1,
  "userId": 999
}
``` 
- Nhấn Send message để gửi thông điệp vào hàng đợi.

Sau khi gửi thành công, Amazon SQS sẽ kích hoạt AWS Lambda thông qua Trigger đã được cấu hình. Tiếp theo, mở dịch vụ AWS Lambda, chọn Function flashsale-ticket-worker, chuyển sang tab Monitor và nhấn View CloudWatch logs để kiểm tra kết quả xử lý.

Nếu trong CloudWatch Logs xuất hiện thông báo tương tự:

[THÀNH CÔNG] User 999 đã mua vé 1

thì có thể kết luận rằng luồng xử lý giữa Amazon SQS, AWS Lambda, Amazon RDS và AWS Secrets Manager đã hoạt động chính xác. Đây là bước xác nhận cuối cùng cho thấy kiến trúc Serverless của hệ thống đặt vé sự kiện đã được triển khai thành công.



![lambda-code](/images/5-Workshop/5.3-S3-vpc/10.jpg)
