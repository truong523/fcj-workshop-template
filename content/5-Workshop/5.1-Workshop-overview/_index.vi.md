---
title : "Giới thiệu "
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu đề tài Trang Đặt Vé Sự Kiện

Trong workshop này, nhóm thực hiện xây dựng hệ thống **Trang Đặt Vé Sự Kiện Giới Hạn trên nền tảng Amazon Web Services (AWS)** theo mô hình **Serverless** nhằm giải quyết bài toán xử lý lượng lớn yêu cầu đặt vé trong thời gian ngắn.

Hệ thống sử dụng các dịch vụ của AWS để tự động mở rộng tài nguyên, tăng khả năng chịu tải và đảm bảo việc đặt vé diễn ra chính xác, an toàn.

Mục tiêu của đề tài:

+ Xây dựng hệ thống đặt vé trực tuyến có khả năng xử lý đồng thời hàng nghìn yêu cầu từ người dùng.
+ Sử dụng Amazon SQS để xếp hàng các yêu cầu đặt vé, hạn chế tình trạng quá tải hệ thống.
+ Sử dụng AWS Lambda kết hợp PostgreSQL Transaction và FOR UPDATE nhằm ngăn chặn hiện tượng bán vượt số lượng vé (Overbooking).
+ Tăng cường bảo mật thông qua IAM, Secrets Manager và CloudFront.
+ Tận dụng kiến trúc Serverless để giảm chi phí triển khai và vận hành hệ thống.

#### Tổng quan về workshop
Trong workshop này, hệ thống được triển khai hoàn toàn trên nền tảng Amazon Web Services (AWS) theo kiến trúc **Serverless Event-Driven.** Mỗi dịch vụ đảm nhận một chức năng riêng nhằm đảm bảo khả năng mở rộng, tính sẵn sàng và hiệu năng của hệ thống.

Kiến trúc tổng thể của hệ thống bao gồm:

+ **Amazon CloudFront** 
+ **AWS WAF** 
+ **AWS Amplify Hosting** 
+ **Amazon Cognito** 
+ **Amazon API**
+ **Amazon SQS**
+ **AWS Lambda** 
+ **Amazon RDS** 
+ **Amazon SES**
+ **Amazon CloudWatch** 
+ **IAM, Secrets Manager, CloudTrail, AWS X-Ray, AWS Budgets** và **CloudFormation** 
Hệ thống được thiết kế nhằm đảm bảo khả năng xử lý lượng lớn yêu cầu trong các chương trình Flash Sale, giảm thiểu hiện tượng nghẽn hệ thống và đảm bảo mỗi vé chỉ được bán đúng số lượng quy định..

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram.jpg)
