---
title : "Cấp quyền truy cập AWS Secrets Manager"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b>5.3.6.</b> "
---

#### Cấp quyền truy cập AWS Secrets Manager

Sau khi tạo cơ sở dữ liệu Amazon RDS, thông tin đăng nhập của cơ sở dữ liệu được lưu trữ trong **AWS Secrets Manager** nhằm tăng cường tính bảo mật. Để AWS Lambda có thể truy xuất mật khẩu và thông tin kết nối cơ sở dữ liệu trong quá trình thực thi, cần cấp quyền truy cập vào AWS Secrets Manager cho Lambda thông qua IAM Role.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console**, mở dịch vụ **AWS Lambda**.
- Chọn hàm Lambda đã tạo trước đó, ví dụ **flashsale-ticket-worker**.
- Chuyển sang tab **Configuration** và chọn **Permissions**.
- Trong phần **Execution role**, nhấn vào tên IAM Role của Lambda để mở trang quản lý IAM.


Tại giao diện IAM Role, tiến hành cấp quyền như sau:

- Nhấn **Add permissions**.
- Chọn **Attach policies**.
- Trong ô tìm kiếm, nhập **SecretsManagerReadWrite**.
- Chọn chính sách **SecretsManagerReadWrite**.
- Nhấn **Add permissions** để hoàn tất việc gán quyền.


Sau khi chính sách được gán thành công, AWS Lambda sẽ có quyền truy cập vào AWS Secrets Manager để đọc thông tin xác thực của Amazon RDS trong quá trình xử lý yêu cầu.

Việc sử dụng AWS Secrets Manager giúp loại bỏ việc lưu trữ trực tiếp tên đăng nhập và mật khẩu trong mã nguồn, đồng thời nâng cao tính bảo mật và đáp ứng nguyên tắc quản lý thông tin xác thực an toàn trong các hệ thống Serverless trên AWS.

![policy-success](/images/5-Workshop/5.3-S3-vpc/srm.jpg)