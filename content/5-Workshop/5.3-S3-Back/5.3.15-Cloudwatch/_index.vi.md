---
title : "Thực hiện Stress Test bằng Bash Script"
date : 2024-01-01
weight : 15
chapter : false
pre : " <b>5.3.15.</b> "
---

#### Thực hiện Stress Test bằng Bash Script

Sau khi hoàn tất việc cấu hình hệ thống, bước tiếp theo là kiểm tra khả năng xử lý đồng thời của kiến trúc Serverless bằng cách gửi một số lượng lớn thông điệp vào Amazon SQS. AWS CloudShell đã được tích hợp sẵn **AWS CLI** và tự động sử dụng quyền của tài khoản hiện tại, vì vậy không cần cài đặt thêm công cụ hay viết chương trình Node.js để thực hiện kiểm thử.

Các bước thực hiện như sau:

- Truy cập **AWS CloudShell** từ thanh công cụ của **AWS Management Console**.
- Tại cửa sổ dòng lệnh, sao chép và dán đoạn **Bash Script** dùng để gửi hàng loạt thông điệp đến hàng đợi Amazon SQS.
- Nhấn **Enter** để bắt đầu thực thi lệnh.
- Quan sát quá trình thực hiện, mỗi lần gửi thành công sẽ trả về thông tin **MessageId**, xác nhận thông điệp đã được đưa vào hàng đợi Amazon SQS.

Ví dụ đoạn Bash Script:

```bash
for i in {1..1000}
do
  aws sqs send-message \
    --queue-url https://sqs.ap-southeast-1.amazonaws.com/ACCOUNT_ID/flashsale-booking-queue \
    --message-body "{\"ticketId\":1,\"userId\":$i}"
done
```

> **Lưu ý:** Thay `ACCOUNT_ID` bằng mã tài khoản AWS của bạn và sử dụng đúng **Queue URL** của hàng đợi đã tạo.

![cloudshell-stress-test](/images/5-Workshop/5.3-S3-vpc/15.1.jpg)

![cloudshell-stress-test](/images/5-Workshop/5.3-S3-vpc/15.2.jpg)

Sau khi Bash Script hoàn thành, Amazon SQS sẽ nhận đồng thời nhiều thông điệp, từ đó kích hoạt nhiều phiên thực thi AWS Lambda để xử lý yêu cầu đặt vé. Đây là bước kiểm tra khả năng chịu tải của hệ thống trước khi đánh giá kết quả xử lý trong các bước tiếp theo.