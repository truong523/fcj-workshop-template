---
title : "Kiểm thử API Flashsale Ticket"
date : 2024-01-01
weight : 17
chapter : false
pre : " <b>5.3.17.</b> "
---

#### Kiểm thử API Flashsale Ticket

Sau khi triển khai thành công Amazon API Gateway, bước tiếp theo là kiểm tra khả năng tiếp nhận yêu cầu đặt vé của hệ thống. Việc kiểm thử được thực hiện bằng **Postman**, giúp xác nhận API có thể nhận dữ liệu từ phía người dùng và chuyển thành công thông điệp vào hàng đợi Amazon SQS.

Mục tiêu của API là tiếp nhận yêu cầu đặt vé Flashsale từ phía người dùng, sau đó chuyển yêu cầu vào **Amazon SQS** để AWS Lambda xử lý bất đồng bộ. Nhờ đó, thời gian phản hồi của hệ thống rất nhanh do người dùng không phải chờ quá trình ghi dữ liệu trực tiếp vào cơ sở dữ liệu.

### Cấu hình Request

Thiết lập yêu cầu trên Postman với các thông số sau:

- **HTTP Method:** `POST`
- **Request URL:**

```text
https://7c4kyholj0.execute-api.ap-southeast-1.amazonaws.com/prod/buy
```

- **Headers**

```text
Content-Type: application/json
```

### Request Body

Chọn **Body** → **raw** → **JSON**, sau đó nhập nội dung sau:

```json
{
    "ticketId": 1,
    "userId": 8888
}
```

Ý nghĩa các tham số:

- **ticketId:** Mã định danh của loại vé cần đặt (ví dụ: `1` tương ứng với vé VIP).
- **userId:** Mã định danh của người dùng thực hiện đặt vé.

![postman-request](/images/5-Workshop/5.3-S3-vpc/postman-request.png)

### Kiểm tra kết quả

Sau khi nhấn **Send**, nếu hệ thống hoạt động bình thường, Postman sẽ trả về mã trạng thái:

```text
Status: 200 OK
```

Phản hồi trả về có dạng JSON như sau:

```json
{
  "SendMessageResponse": {
    "ResponseMetadata": {
      "RequestId": "2bebfec7-a03a-5b93-8922-9c1e650030d4"
    },
    "SendMessageResult": {
      "MD5OfMessageBody": "799e1eb079ffb4d24bccff0b23f52ed75",
      "MessageId": "11dd0785-a895-48b9-a180-d2e0fd3adfc3"
    }
  }
}
```

![postman-response](/images/5-Workshop/5.3-S3-vpc/17.jpg)

### Giải thích kết quả trả về

Các trường dữ liệu trong phản hồi có ý nghĩa như sau:

- **SendMessageResponse:** Thông tin xác nhận yêu cầu đã được Amazon SQS tiếp nhận thành công.
- **RequestId:** Mã định danh của phiên xử lý do AWS API Gateway tạo ra.
- **MessageId:** Mã định danh duy nhất của thông điệp trong hàng đợi Amazon SQS. Đây là bằng chứng cho thấy yêu cầu đặt vé đã được đưa vào hàng đợi để AWS Lambda xử lý.
- **MD5OfMessageBody:** Giá trị băm MD5 của nội dung thông điệp nhằm kiểm tra tính toàn vẹn của dữ liệu trong quá trình truyền tải.

Khi nhận được phản hồi **HTTP Status 200 OK** cùng với **MessageId**, có thể kết luận rằng API Gateway đã chuyển thành công yêu cầu đặt vé vào Amazon SQS. Sau đó, AWS Lambda sẽ tự động nhận thông điệp từ hàng đợi và tiếp tục xử lý nghiệp vụ đặt vé theo kiến trúc Serverless của hệ thống.