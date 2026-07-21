---
title : "Cập nhật thông tin cấu hình vào AWS Lambda"
date : 2024-01-01
weight : 13
chapter : false
pre : " <b>5.3.13.</b> "
---

#### Cập nhật thông tin cấu hình vào AWS Lambda

Sau khi thu thập được **RDS Endpoint** và **Secret Name** từ AWS, bước tiếp theo là cập nhật các thông tin này vào mã nguồn của AWS Lambda. Việc cấu hình đúng các giá trị này giúp Lambda có thể kết nối đến Amazon RDS và truy xuất thông tin đăng nhập từ AWS Secrets Manager khi thực thi.

Các bước thực hiện như sau:

- Truy cập **AWS Management Console** và mở dịch vụ **AWS Lambda**.
- Chọn Function **flashsale-ticket-worker**.
- Chuyển sang tab **Code** và mở tệp **index.js**.
- Tìm giá trị **ĐIỀN_ENDPOINT_RDS_VÀO_ĐÂY** và thay bằng **RDS Endpoint** đã sao chép ở bước trước.
- Tìm giá trị **TÊN_SECRET_CỦA_BẠN** và thay bằng **Secret Name** đã lấy từ AWS Secrets Manager.
- Sau khi cập nhật hoàn tất, nhấn nút **Deploy** để lưu và triển khai phiên bản mã nguồn mới.


Sau khi triển khai thành công, AWS Lambda sẽ hiển thị thông báo **Successfully updated the function**. Điều này xác nhận rằng các thay đổi trong mã nguồn đã được lưu và sẵn sàng sử dụng trong quá trình xử lý yêu cầu đặt vé.

![lambda-update-config](/images/5-Workshop/5.3-S3-vpc/13.1.jpg)


![lambda-deploy-success](/images/5-Workshop/5.3-S3-vpc/13.2.jpg)

Việc cập nhật chính xác **RDS Endpoint** và **Secret Name** giúp AWS Lambda thiết lập kết nối an toàn đến Amazon RDS thông qua AWS Secrets Manager, đảm bảo thông tin xác thực không được lưu trực tiếp trong mã nguồn và nâng cao tính bảo mật của hệ thống.