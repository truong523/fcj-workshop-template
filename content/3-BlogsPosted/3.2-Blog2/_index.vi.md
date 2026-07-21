---
title: "Blog 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b>3.2.</b> "
---


# Amazon SQS – Khi tốc độ không phải là tất cả

Khi mới bắt đầu tìm hiểu về Amazon Web Services (AWS), mình từng nghĩ rằng một hệ thống tốt là hệ thống có thể xử lý yêu cầu càng nhanh càng tốt. API nhận request, xử lý ngay và trả kết quả ngay nghe có vẻ là phương án tối ưu.

Tuy nhiên, khi thử xây dựng một hệ thống mô phỏng **Flash Sale Ticket Booking** với hàng nghìn người dùng gửi yêu cầu đặt vé cùng một thời điểm, mình nhận ra rằng **tốc độ không phải là yếu tố quan trọng nhất**. Điều quan trọng hơn là hệ thống có thể xử lý tất cả yêu cầu **một cách ổn định và không làm mất dữ liệu**.

Đó cũng là lúc mình hiểu rõ hơn vai trò của **Amazon Simple Queue Service (Amazon SQS)**.

Thay vì xử lý trực tiếp mọi yêu cầu ngay khi nhận được, Amazon SQS hoạt động như một **hàng đợi thông điệp (Message Queue)**. Mỗi request sẽ được lưu an toàn trong Queue trước, sau đó các Worker (ví dụ AWS Lambda) sẽ lần lượt lấy từng message để xử lý.

Cách tiếp cận này giúp hệ thống hoạt động ổn định ngay cả khi số lượng người dùng tăng đột biến.

## Những lợi ích mình nhận thấy khi sử dụng Amazon SQS

- Hệ thống không bị quá tải khi có lượng truy cập lớn trong thời gian ngắn.
- Nếu dịch vụ xử lý phía sau gặp lỗi hoặc tạm thời không hoạt động, các message vẫn được lưu trong Queue và không bị mất.
- Có thể mở rộng số lượng Worker hoặc Lambda để tăng khả năng xử lý mà không cần thay đổi phía Client.
- Giảm sự phụ thuộc giữa các thành phần của hệ thống (Decoupling), giúp việc bảo trì và mở rộng trở nên dễ dàng hơn.

Điều mình thích nhất ở Amazon SQS không phải là khả năng xử lý nhanh, mà là **khả năng giúp hệ thống luôn ổn định trong những tình huống tải cao**.

Trước đây mình thường đặt câu hỏi:

> *Làm thế nào để xử lý request nhanh nhất?*

Sau khi tìm hiểu về kiến trúc Event-Driven trên AWS, mình lại có một góc nhìn khác:

> *Nếu có thêm 10.000 request trong cùng một phút thì hệ thống sẽ phản ứng như thế nào?*

Chỉ một thay đổi nhỏ trong tư duy thiết kế cũng dẫn đến cách xây dựng hệ thống hoàn toàn khác.

Theo mình, Amazon SQS không chỉ phù hợp với các hệ thống lớn mà còn rất hữu ích cho nhiều ứng dụng thực tế như:

- Flash Sale Ticket Booking
- Website thương mại điện tử
- Gửi Email bất đồng bộ
- Xử lý hình ảnh hoặc video
- Đồng bộ dữ liệu giữa các hệ thống
- Event-Driven Microservices
- AI Workflow và Background Jobs

Không phải lúc nào xử lý ngay cũng là lựa chọn tốt nhất.

Đôi khi, để hệ thống vận hành ổn định hơn, điều cần làm chỉ đơn giản là **để các yêu cầu biết xếp hàng**.

Đó cũng là bài học thú vị nhất mà mình rút ra khi tìm hiểu và thực hành với **Amazon SQS** trên nền tảng AWS.

---

## Hình minh họa

![Ảnh của bạn](/images/3-Blog/Blog2.jpg)

*Nguồn: Amazon Web Services*

---

## Tài liệu tham khảo

- Amazon SQS Turns 20: Two Decades of Reliable Messaging at Scale  
  https://aws.amazon.com/blogs/aws/amazon-sqs-turns-20-two-decades-of-reliable-messaging-at-scale/

- Amazon SQS Documentation  
  https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html

- Amazon SQS Product Page  
  https://aws.amazon.com/sqs/