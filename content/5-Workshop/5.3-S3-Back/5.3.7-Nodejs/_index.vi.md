---
title : "Triển khai mã nguồn AWS Lambda"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b>5.3.7.</b> "
---

#### Triển khai mã nguồn AWS Lambda

Sau khi hoàn tất việc cấu hình các dịch vụ AWS, bước tiếp theo là triển khai mã nguồn xử lý nghiệp vụ đặt vé lên AWS Lambda. Hệ thống sử dụng ngôn ngữ **Node.js** kết hợp với thư viện **node-postgres (pg)** để kết nối và thao tác với cơ sở dữ liệu Amazon RDS PostgreSQL.

Do môi trường thực thi của AWS Lambda không tích hợp sẵn thư viện **pg**, cần cài đặt thư viện này trên máy tính trước khi đóng gói và triển khai mã nguồn.

Các bước thực hiện như sau:

- Trên máy tính, mở **Command Prompt** hoặc **Terminal**.
- Di chuyển đến thư mục chứa dự án Lambda.
- Thực hiện lệnh sau để cài đặt thư viện PostgreSQL:

```bash
npm install pg
```

Sau khi cài đặt hoàn tất, trong thư mục dự án sẽ xuất hiện các tệp và thư mục như:

- `node_modules`
- `package.json`
- `package-lock.json`

Tiếp theo, tiến hành tạo tệp mã nguồn của Lambda:

- Mở thư mục dự án, ví dụ:

```text
C:\Users\Acer\flashsale-worker
```

- Tạo tệp mới có tên **index.js**.
- Mở tệp **index.js** bằng Visual Studio Code hoặc trình soạn thảo văn bản.
- Sao chép toàn bộ mã nguồn xử lý nghiệp vụ đặt vé và lưu vào tệp **index.js**.


#### Đóng gói mã nguồn

Sau khi hoàn thành mã nguồn, cần đóng gói dự án thành tệp ZIP để triển khai lên AWS Lambda.

Lưu ý, chỉ nén **toàn bộ nội dung bên trong thư mục dự án**, không nén chính thư mục chứa dự án.

Các bước thực hiện:

- Mở thư mục dự án **flashsale-worker**.
- Chọn toàn bộ các tệp và thư mục, bao gồm:

  - `index.js`
  - `node_modules`
  - `package.json`
  - `package-lock.json`

- Nhấn chuột phải và chọn **Compress to ZIP file** hoặc **Add to archive...** (định dạng ZIP).
- Đặt tên tệp nén là **deploy.zip**.

![zip-file](/images/5-Workshop/5.3-S3-vpc/deploy.jpg)

#### Triển khai lên AWS Lambda

Sau khi tạo tệp **deploy.zip**, tiến hành tải mã nguồn lên AWS Lambda.

Các bước thực hiện như sau:

- Truy cập **AWS Lambda** và chọn Function **flashsale-ticket-worker**.
- Chọn tab **Code**.
- Nhấn **Upload from** → **.zip file**.
- Chọn tệp **deploy.zip** vừa tạo.
- Nhấn **Save** để hoàn tất quá trình triển khai.

Khi quá trình tải lên thành công, AWS Lambda sẽ sử dụng mã nguồn mới trong các lần thực thi tiếp theo.

![upload-code](/images/5-Workshop/5.3-S3-vpc/upload-code.png)