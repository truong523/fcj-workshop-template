---
title: "Blog 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b>3.3.</b> "
---

=
# Trọng tâm An ninh mạng: Bảo vệ Nhận diện và AI trong kỷ nguyên Cloud

Trong những năm gần đây, trọng tâm của an ninh mạng trên nền tảng điện toán đám mây đã có nhiều thay đổi. Nếu trước đây việc bảo mật chủ yếu tập trung vào tường lửa, mạng hay phân quyền IAM, thì hiện nay **bảo vệ danh tính (Identity)** và **kiểm soát các ứng dụng AI** đang trở thành những yếu tố quan trọng trong kiến trúc bảo mật hiện đại.

Dựa trên các cập nhật từ **AWS Security Blog**, dưới đây là một số xu hướng nổi bật mà các kỹ sư Cloud và DevSecOps cần quan tâm.

---

## 1. Tăng cường bảo vệ danh tính với Amazon Cognito

Danh tính người dùng hiện là mục tiêu tấn công phổ biến đối với các ứng dụng Web và Mobile.

Nếu kẻ tấn công đánh cắp được Refresh Token, chúng có thể tìm cách duy trì quyền truy cập trái phép trong một khoảng thời gian nhất định.

Để giảm thiểu rủi ro này, AWS khuyến nghị:

- Kích hoạt **Refresh Token Rotation** để mỗi lần sử dụng Refresh Token sẽ sinh ra một token mới và vô hiệu hóa token cũ.
- Giảm thời gian sống (**Time-To-Live - TTL**) của Refresh Token nhằm hạn chế thời gian kẻ tấn công có thể lợi dụng.
- Theo dõi các hoạt động đăng nhập bất thường và thường xuyên kiểm tra lịch sử xác thực của người dùng.

Những biện pháp này giúp tăng cường mô hình **Zero Trust Identity**, giảm nguy cơ bị chiếm quyền truy cập.

---

## 2. Kiểm soát AI bằng Cedar Policy

Sự phát triển của **Agentic AI** giúp các hệ thống AI có thể tự động thực hiện nhiều tác vụ như gọi API, truy cập cơ sở dữ liệu hoặc tương tác với các dịch vụ khác.

Điều này cũng đặt ra yêu cầu phải kiểm soát chặt chẽ quyền hạn của AI.

AWS giới thiệu việc sử dụng **Cedar** (ngôn ngữ phân quyền của Amazon Verified Permissions) kết hợp với **Amazon Bedrock AgentCore** để xây dựng mô hình **Policy-as-Code**.

Cách tiếp cận này mang lại nhiều lợi ích:

- Xác định rõ AI được phép thực hiện những hành động nào.
- Giảm nguy cơ Prompt Injection khiến AI thực hiện các thao tác ngoài ý muốn.
- Quản lý quyền truy cập tập trung và minh bạch.
- Nâng cao mức độ an toàn cho các ứng dụng AI.

Thay vì chỉ dựa vào Prompt, mọi yêu cầu của AI đều cần được kiểm tra thông qua Policy trước khi thực hiện.

---

## 3. Bảo vệ hệ thống bằng AWS WAF Bot Control

Sự phát triển của AI cũng kéo theo sự xuất hiện của nhiều loại bot tự động có khả năng thu thập dữ liệu hoặc tấn công API.

AWS WAF Bot Control hỗ trợ phân loại lưu lượng truy cập để nhận biết:

- **Verified AI Agents:** Các AI Agent hợp lệ và được xác thực.
- **Malicious Bots:** Các bot thu thập dữ liệu, dò quét lỗ hổng hoặc thực hiện tấn công Brute-force.

Dựa trên kết quả phân tích hành vi, AWS WAF có thể tự động:

- Cho phép truy cập (Allow)
- Yêu cầu xác minh (Challenge)
- Chặn truy cập (Block)

Nhờ đó, hệ thống phía sau như **AWS Lambda**, **Amazon API Gateway** hay **Amazon Aurora** được bảo vệ tốt hơn trước các cuộc tấn công tự động và giảm nguy cơ phát sinh chi phí không cần thiết.

---

## Kết luận

An ninh mạng trên AWS ngày nay không chỉ dừng lại ở việc cấu hình IAM hay triển khai tường lửa.

Để xây dựng một hệ thống Cloud an toàn, các tổ chức cần kết hợp nhiều lớp bảo vệ như:

- Bảo vệ danh tính người dùng.
- Áp dụng mô hình **Policy-as-Code** cho AI.
- Giám sát các hoạt động đăng nhập bất thường.
- Kiểm soát lưu lượng truy cập bằng AWS WAF Bot Control.

Việc kết hợp các giải pháp trên sẽ giúp hệ thống có khả năng phòng thủ tốt hơn trước những mối đe dọa ngày càng phức tạp trong kỷ nguyên AI.

---

## Hình minh họa

![AWS WAF Bot Control](/images/3-Blog/Blog3.jpg)

*Nguồn: Amazon Web Services*

---

## Tài liệu tham khảo

- **Authenticate legitimate AI agent traffic with AWS WAF Bot Control**  
  https://aws.amazon.com/blogs/security/authenticate-legitimate-ai-agent-traffic-with-aws-waf-bot-control/

- **AWS Security Blog**  
  https://aws.amazon.com/blogs/security/