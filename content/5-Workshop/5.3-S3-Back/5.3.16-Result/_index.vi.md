---
title : "Cấu hình Amazon API Gateway"
date : 2024-01-01
weight : 16
chapter : false
pre : " <b>5.3.16.</b> "
---

#### Cấu hình Amazon API Gateway

Sau khi hoàn tất việc xây dựng hệ thống xử lý phía sau bằng Amazon SQS và AWS Lambda, bước tiếp theo là tạo một **REST API** bằng **Amazon API Gateway** để tiếp nhận yêu cầu đặt vé từ phía người dùng. API Gateway sẽ nhận các yêu cầu HTTP từ ứng dụng khách, sau đó chuyển trực tiếp dữ liệu vào hàng đợi Amazon SQS mà không cần thông qua một hàm Lambda trung gian, giúp tối ưu hiệu năng và giảm chi phí vận hành.

Các bước thực hiện như sau:

##### 1. Tạo REST API

- Truy cập **AWS Management Console** và mở dịch vụ **Amazon API Gateway**.
- Chọn **Create API**.
- Trong mục **REST API**, nhấn **Build**.
- Chọn **New API**.
- Đặt tên API là **flashsale-api**.
- Nhấn **Create API**.


##### 2. Tạo tài nguyên `/buy`

- Chọn **Actions** → **Create Resource**.
- Tại **Resource Name**, nhập `buy`.
- Nhấn **Create Resource**.
- Chọn tài nguyên **/buy** vừa tạo.
- Chọn **Actions** → **Create Method**.
- Chọn phương thức **POST** và nhấn dấu **✓** để xác nhận.


##### 3. Cấu hình tích hợp với Amazon SQS

Trong phần cấu hình của phương thức **POST**, thiết lập các thông số sau:

- **Integration type:** AWS Service.
- **AWS Region:** `ap-southeast-1`.
- **AWS Service:** Simple Queue Service (SQS).
- **HTTP method:** POST.
- **Action Type:** Use path override.
- **Path override:** `274118253697/flashsale-booking-queue`.
- **Execution role:** Nhập ARN của IAM Role có quyền truy cập Amazon SQS.


##### 4. Thiết lập Mapping Template

Để API Gateway chuyển đổi dữ liệu JSON từ phía người dùng sang định dạng mà Amazon SQS có thể xử lý, thực hiện như sau:

- Chọn **Integration Request**.
- Trong mục **Mapping Templates**, nhấn **Add mapping template**.
- Tại **Content-Type**, nhập:

```text
application/json
```

- Trong phần **Template Body**, nhập đoạn mã sau:

```text
Action=SendMessage&MessageBody=$util.urlEncode($input.body)
```

- Nhấn **Save** để lưu cấu hình.


##### 5. Triển khai API

Sau khi hoàn tất cấu hình:

- Chọn **Actions** → **Deploy API**.
- Chọn **[New Stage]**.
- Đặt tên Stage là **prod**.
- Nhấn **Deploy**.

Sau khi triển khai thành công, API Gateway sẽ cung cấp một địa chỉ **Invoke URL**, ví dụ:

```text
https://xxxx.execute-api.ap-southeast-1.amazonaws.com/prod
```

Địa chỉ này sẽ được sử dụng để ứng dụng gửi yêu cầu đặt vé đến hệ thống.

![deploy-api](/images/5-Workshop/5.3-S3-vpc/16.jpg)

Sau khi API được triển khai thành công, người dùng có thể gửi yêu cầu HTTP POST đến endpoint `/buy`. Amazon API Gateway sẽ tự động chuyển đổi dữ liệu và đưa thông điệp vào Amazon SQS. Từ đó, AWS Lambda sẽ nhận thông điệp từ hàng đợi và xử lý nghiệp vụ đặt vé theo kiến trúc Serverless của hệ thống.