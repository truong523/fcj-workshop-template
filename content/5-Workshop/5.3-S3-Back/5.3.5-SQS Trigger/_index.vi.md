---
title : "Kết nối Amazon SQS với AWS Lambda"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b>5.3.5.</b> "
---

#### Cấu hình Trigger Amazon SQS cho AWS Lambda

Sau khi hoàn tất việc tạo hàng đợi Amazon SQS và cấp quyền cho AWS Lambda, bước tiếp theo là cấu hình **Trigger** để Lambda tự động xử lý các thông điệp được gửi đến hàng đợi.

Trigger đóng vai trò kết nối giữa Amazon SQS và AWS Lambda. Khi có một yêu cầu đặt vé được gửi vào hàng đợi, AWS Lambda sẽ tự động được kích hoạt để xử lý yêu cầu mà không cần can thiệp thủ công.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console**, mở dịch vụ **AWS Lambda**.
- Chọn hàm Lambda đã tạo trước đó, ví dụ **flashsale-ticket-worker**.
- Trong phần **Function overview**, nhấn **+ Add trigger** để thêm bộ kích hoạt.


Tại màn hình cấu hình Trigger, thực hiện các thiết lập sau:

- **Select a source:** Chọn **Amazon SQS**.
- **SQS Queue:** Chọn hàng đợi **flashsale-booking-queue** đã tạo ở bước trước.
- **Batch size:** Đặt giá trị là **1** để Lambda xử lý từng thông điệp riêng lẻ, giúp hạn chế tình trạng xử lý đồng thời nhiều yêu cầu và giảm nguy cơ bán vượt số lượng vé (Overbooking).


Sau khi hoàn tất cấu hình, cuộn xuống cuối trang và nhấn **Add** để kích hoạt Trigger.

Khi Trigger được tạo thành công, Amazon SQS sẽ tự động kích hoạt AWS Lambda mỗi khi có thông điệp mới trong hàng đợi. Đây là cơ chế giúp hệ thống xử lý các yêu cầu đặt vé theo mô hình bất đồng bộ (Asynchronous Processing), góp phần tăng khả năng chịu tải và đảm bảo hệ thống hoạt động ổn định trong các đợt mở bán vé với lượng truy cập lớn.

![trigger-success](/images/5-Workshop/5.3-S3-vpc/trigger.jpg)