---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b>2.</b> "
---


# Hệ thống Đặt Vé Sự Kiện Giới Hạn trên nền tảng AWS Serverless

## Giải pháp AWS Serverless cho hệ thống Flash Sale Ticket

### 1. Tóm tắt điều hành

Hệ thống Đặt Vé Sự Kiện Giới Hạn được xây dựng nhằm giải quyết bài toán xử lý lượng lớn yêu cầu đặt vé trong thời gian rất ngắn. Hệ thống được triển khai theo kiến trúc **AWS Serverless Event-Driven**, cho phép tự động mở rộng tài nguyên, giảm chi phí vận hành và đảm bảo khả năng xử lý đồng thời.

Giải pháp sử dụng **Amazon API Gateway**, **Amazon SQS**, **AWS Lambda**, **Amazon RDS PostgreSQL**, **Amazon SES**, cùng các dịch vụ hỗ trợ như **AWS IAM**, **AWS Secrets Manager** và **Amazon CloudWatch** để xây dựng hệ thống đặt vé có khả năng chống quá tải, chống bán vượt số lượng vé (Overbooking) và gửi email xác nhận sau khi đặt vé thành công.

---

### 2. Tuyên bố vấn đề

#### Vấn đề hiện tại

Trong các chương trình Flash Sale hoặc mở bán vé sự kiện, hàng nghìn người dùng thường truy cập đồng thời khiến hệ thống dễ gặp các vấn đề:

- Máy chủ quá tải.
- Thời gian phản hồi chậm.
- Race Condition khi nhiều người cùng mua một vé.
- Bán vượt số lượng vé.
- Khó mở rộng khi lưu lượng tăng đột biến.

#### Giải pháp

Hệ thống sử dụng kiến trúc **AWS Serverless Event-Driven**.

Quy trình xử lý gồm:

- Amazon API Gateway tiếp nhận yêu cầu đặt vé.
- Amazon SQS lưu trữ yêu cầu vào hàng đợi.
- AWS Lambda xử lý tuần tự từng yêu cầu.
- Amazon RDS PostgreSQL sử dụng Transaction kết hợp **SELECT ... FOR UPDATE** để khóa dữ liệu và tránh bán vượt số lượng vé.
- Amazon SES gửi Email xác nhận cho khách hàng sau khi đặt vé thành công.

#### Lợi ích

Giải pháp giúp:

- Chịu tải hàng nghìn người dùng đồng thời.
- Ngăn chặn Overbooking.
- Tự động mở rộng theo số lượng request.
- Không cần quản lý máy chủ.
- Chi phí vận hành thấp theo mô hình Pay-as-you-go.
- Đảm bảo an toàn dữ liệu và bảo mật thông tin.

---

### 3. Kiến trúc giải pháp

Hệ thống được triển khai theo kiến trúc Serverless trên Amazon Web Services.
 
![overview](/images/5-Workshop/5.1-Workshop-overview/diagram.jpg)

#### Dịch vụ AWS sử dụng

- **Amazon CloudFront:** Phân phối nội dung Website.
- **AWS WAF:** Bảo vệ Website khỏi các cuộc tấn công.
- **AWS Amplify:** Triển khai giao diện Website.
- **Amazon Cognito:** Xác thực người dùng.
- **Amazon API Gateway:** Tiếp nhận yêu cầu HTTP.
- **Amazon SQS:** Hàng đợi xử lý yêu cầu đặt vé.
- **AWS Lambda:** Xử lý nghiệp vụ đặt vé.
- **Amazon RDS PostgreSQL:** Lưu trữ dữ liệu.
- **AWS Secrets Manager:** Quản lý thông tin kết nối Database.
- **Amazon SES:** Gửi Email xác nhận.
- **Amazon CloudWatch:** Theo dõi Log và hiệu năng.
- **AWS IAM:** Phân quyền giữa các dịch vụ AWS.

#### Thiết kế thành phần

- **Frontend:** Website đặt vé được triển khai bằng AWS Amplify.
- **API Layer:** Amazon API Gateway tiếp nhận yêu cầu đặt vé.
- **Message Queue:** Amazon SQS lưu trữ yêu cầu trước khi xử lý.
- **Business Logic:** AWS Lambda xử lý nghiệp vụ đặt vé.
- **Database:** Amazon RDS PostgreSQL lưu thông tin người dùng và vé.
- **Notification:** Amazon SES gửi Email xác nhận.
- **Monitoring:** Amazon CloudWatch giám sát hệ thống.

---

### 4. Triển khai kỹ thuật

Dự án được triển khai theo các giai đoạn sau:

1. Thiết kế kiến trúc hệ thống.
2. Triển khai Amazon RDS PostgreSQL.
3. Tạo AWS Lambda.
4. Cấu hình Amazon SQS.
5. Thiết lập IAM và Secrets Manager.
6. Kết nối Lambda với SQS.
7. Triển khai mã nguồn Node.js.
8. Tạo REST API bằng Amazon API Gateway.
9. Xây dựng giao diện Website.
10. Kiểm thử API bằng Postman.
11. Stress Test với CloudShell và Bash Script.
12. Gửi Email xác nhận bằng Amazon SES.

#### Yêu cầu kỹ thuật

- HTML5, CSS3, JavaScript.
- Node.js.
- PostgreSQL.
- AWS Lambda.
- Amazon API Gateway.
- Amazon SQS.
- Amazon RDS.
- Amazon SES.
- AWS Amplify.
- Amazon Cognito.
- AWS IAM.
- AWS CloudWatch.

---

### 5. Lộ trình triển khai

| Giai đoạn | Nội dung |
|-----------|----------|
| Tuần 1 | Thiết kế kiến trúc hệ thống |
| Tuần 2 | Triển khai Amazon RDS |
| Tuần 3 | Xây dựng AWS Lambda |
| Tuần 4 | Cấu hình Amazon SQS |
| Tuần 5 | IAM và Secrets Manager |
| Tuần 6 | API Gateway |
| Tuần 7 | Xây dựng giao diện Website |
| Tuần 8 | Kiểm thử API |
| Tuần 9 | Stress Test |
| Tuần 10 | Gửi Email bằng Amazon SES |

---

### 6. Ước tính ngân sách

Chi phí triển khai chủ yếu dựa trên AWS Free Tier.

#### Chi phí hạ tầng

- Amazon RDS PostgreSQL
- AWS Lambda
- Amazon API Gateway
- Amazon SQS
- Amazon SES
- AWS Amplify
- Amazon CloudWatch

**Tổng chi phí dự kiến:** khoảng **0–10 USD/tháng** (tùy theo số lượng request và email gửi), phù hợp cho mục đích học tập và nghiên cứu.

---

### 7. Đánh giá rủi ro

#### Ma trận rủi ro

- Quá tải hệ thống.
- Race Condition.
- Overbooking.
- Lộ thông tin Database.
- Chi phí AWS vượt dự kiến.

#### Chiến lược giảm thiểu

- Amazon SQS xử lý hàng đợi.
- PostgreSQL Transaction và SELECT FOR UPDATE.
- AWS Secrets Manager lưu thông tin Database.
- IAM phân quyền theo Principle of Least Privilege.
- CloudWatch theo dõi hệ thống.
- AWS Budgets cảnh báo chi phí.

#### Kế hoạch dự phòng

- Sao lưu cơ sở dữ liệu định kỳ.
- Khôi phục tài nguyên bằng AWS CloudFormation.
- Theo dõi và xử lý lỗi qua CloudWatch Logs.

---

### 8. Kết quả kỳ vọng

#### Cải tiến kỹ thuật

- Xử lý hàng nghìn yêu cầu đặt vé đồng thời.
- Không xảy ra hiện tượng bán vượt số lượng vé.
- Tự động mở rộng theo lượng truy cập.
- Giảm đáng kể chi phí vận hành.

#### Giá trị dài hạn

- Là mô hình Serverless hoàn chỉnh phục vụ học tập và nghiên cứu.
- Có thể mở rộng thành hệ thống bán vé trực tuyến thực tế.
- Dễ dàng bổ sung các chức năng như thanh toán trực tuyến, quản lý sự kiện và Dashboard thống kê trong tương lai.