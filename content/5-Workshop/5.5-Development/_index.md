---
title: "Evaluation"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b>5.5.</b> "
---

## Achievements

After completing the workshop, the system successfully implemented an **AWS Serverless Event-Driven** architecture for a Flash Sale Ticket Booking application.

The following features were successfully completed:

- Built an **Amazon RDS for PostgreSQL** database to store ticket and user information.
- Deployed **AWS Lambda** to process ticket booking requests.
- Used **Amazon SQS** as a message queue to process booking requests asynchronously.
- Configured **Amazon API Gateway** to receive requests from the website.
- Integrated **AWS Secrets Manager** to securely manage database credentials.
- Sent booking confirmation emails using **Amazon SES**.
- Monitored logs and system execution with **Amazon CloudWatch**.
- Developed the website frontend and deployed it using **AWS Amplify**.
- Tested APIs with Postman and performed stress testing using **AWS CloudShell**.

---

## Advantages

Compared with traditional architectures, the system provides several benefits:

- The Serverless architecture eliminates the need to manage servers.
- Automatically scales based on user demand.
- Amazon SQS reduces system overload during periods of high concurrent traffic.
- AWS Lambda runs only when requests are received, reducing operational costs.
- PostgreSQL transactions combined with `SELECT ... FOR UPDATE` prevent ticket overbooking.
- Amazon SES automatically sends confirmation emails after successful bookings.
- Amazon CloudWatch provides centralized logging and simplifies troubleshooting.

---

## Limitations

Although the system operates reliably, there are still several limitations:

- Online payment functionality has not yet been implemented.
- User authentication with **Amazon Cognito** has not been integrated.
- A real-time dashboard for revenue and ticket statistics is not available.
- The website interface is still basic and has not been fully optimized for mobile devices.

---

## Future Improvements

The system can be further enhanced with the following features:

- Automate infrastructure deployment using **AWS CloudFormation**, **AWS SAM**, or **Terraform**.
- Integrate **Amazon Cognito** for user authentication and authorization.
- Add online payment gateway integration.
- Build analytical dashboards using **Amazon QuickSight**.
- Improve performance and security with **Amazon CloudFront** and **AWS WAF**.
- Support multiple events and multiple ticket categories within a single platform.

---

## Source Code

The complete project source code and demonstration video are available on Google Drive:

**Google Drive link:** https://drive.google.com/drive/folders/1n_aHVtlblb3QDL-7qWoXmRGKMcIJziHT