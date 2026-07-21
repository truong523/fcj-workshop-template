---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b>2.</b> "
---


# Event Ticket Booking System on AWS Serverless

## AWS Serverless Solution for a Flash Sale Ticket Booking System

### 1. Executive Summary

The **Event Ticket Booking System** is designed to solve the challenge of processing a large number of ticket booking requests within a very short period of time. The system is built on an **AWS Serverless Event-Driven Architecture**, enabling automatic scalability, lower operational costs, and efficient concurrent request processing.

The solution utilizes **Amazon API Gateway**, **Amazon SQS**, **AWS Lambda**, **Amazon RDS for PostgreSQL**, **Amazon SES**, together with supporting services such as **AWS IAM**, **AWS Secrets Manager**, and **Amazon CloudWatch** to build a ticket booking platform capable of handling high traffic, preventing overbooking, and sending confirmation emails after successful bookings.

---

## 2. Problem Statement

### Current Challenges

During flash sale campaigns or event ticket releases, thousands of users may access the system simultaneously, causing several issues:

- Server overload.
- Slow response time.
- Race conditions when multiple users purchase the same ticket.
- Ticket overbooking.
- Difficulty scaling under sudden traffic spikes.

### Proposed Solution

The system adopts an **AWS Serverless Event-Driven Architecture**.

The booking workflow is as follows:

- Amazon API Gateway receives ticket booking requests.
- Amazon SQS stores incoming requests in a message queue.
- AWS Lambda processes each request asynchronously.
- Amazon RDS PostgreSQL uses database transactions together with **SELECT ... FOR UPDATE** to lock records and prevent ticket overbooking.
- Amazon SES sends confirmation emails after successful bookings.

### Benefits

This solution provides:

- High scalability for thousands of concurrent users.
- Prevention of ticket overbooking.
- Automatic scaling based on incoming requests.
- No server management required.
- Cost-effective Pay-as-you-go pricing.
- Secure data storage and access control.

---

## 3. Solution Architecture

The system is implemented using an AWS Serverless architecture.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram.jpg)

### AWS Services Used

- **Amazon CloudFront:** Delivers website content globally.
- **AWS WAF:** Protects the website from common web attacks.
- **AWS Amplify:** Hosts and deploys the frontend application.
- **Amazon Cognito:** Provides user authentication and authorization.
- **Amazon API Gateway:** Receives HTTP requests from clients.
- **Amazon SQS:** Queues ticket booking requests.
- **AWS Lambda:** Processes ticket booking business logic.
- **Amazon RDS PostgreSQL:** Stores user, ticket, and booking information.
- **AWS Secrets Manager:** Securely stores database credentials.
- **Amazon SES:** Sends booking confirmation emails.
- **Amazon CloudWatch:** Monitors logs and system performance.
- **AWS IAM:** Manages permissions between AWS services.

### Component Design

- **Frontend:** Event ticket booking website deployed using AWS Amplify.
- **API Layer:** Amazon API Gateway receives ticket booking requests.
- **Message Queue:** Amazon SQS buffers incoming requests.
- **Business Logic:** AWS Lambda processes booking requests.
- **Database:** Amazon RDS PostgreSQL stores application data.
- **Notification Service:** Amazon SES sends confirmation emails.
- **Monitoring:** Amazon CloudWatch collects logs and performance metrics.

---

## 4. Technical Implementation

The project is implemented through the following phases:

1. Design the system architecture.
2. Deploy Amazon RDS PostgreSQL.
3. Create AWS Lambda functions.
4. Configure Amazon SQS.
5. Configure AWS IAM and Secrets Manager.
6. Connect AWS Lambda with Amazon SQS.
7. Deploy the Node.js application.
8. Create a REST API using Amazon API Gateway.
9. Build the website frontend.
10. Test the API using Postman.
11. Perform stress testing using AWS CloudShell and Bash scripts.
12. Configure Amazon SES for email notifications.

### Technical Requirements

- HTML5
- CSS3
- JavaScript
- Node.js
- PostgreSQL
- AWS Lambda
- Amazon API Gateway
- Amazon SQS
- Amazon RDS
- Amazon SES
- AWS Amplify
- Amazon Cognito
- AWS IAM
- Amazon CloudWatch

---

## 5. Implementation Roadmap

| Phase | Activities |
|--------|------------|
| Week 1 | Design the system architecture |
| Week 2 | Deploy Amazon RDS |
| Week 3 | Develop AWS Lambda |
| Week 4 | Configure Amazon SQS |
| Week 5 | Configure IAM and Secrets Manager |
| Week 6 | Configure Amazon API Gateway |
| Week 7 | Develop the website frontend |
| Week 8 | Perform API testing |
| Week 9 | Conduct stress testing |
| Week 10 | Configure Amazon SES for email notifications |

---

## 6. Budget Estimation

The infrastructure is primarily deployed using the AWS Free Tier.

### Infrastructure Costs

- Amazon RDS PostgreSQL
- AWS Lambda
- Amazon API Gateway
- Amazon SQS
- Amazon SES
- AWS Amplify
- Amazon CloudWatch

**Estimated Monthly Cost:** Approximately **USD 0–10 per month**, depending on the number of requests and emails sent. This cost is suitable for educational and research purposes.

---

## 7. Risk Assessment

### Risk Matrix

- System overload.
- Race conditions.
- Ticket overbooking.
- Database credential exposure.
- Unexpected AWS costs.

### Mitigation Strategies

- Amazon SQS for request queue management.
- PostgreSQL transactions with **SELECT FOR UPDATE**.
- AWS Secrets Manager for secure credential storage.
- AWS IAM following the **Principle of Least Privilege**.
- Amazon CloudWatch for monitoring.
- AWS Budgets for cost alerts.

### Contingency Plan

- Perform regular database backups.
- Restore infrastructure using AWS CloudFormation.
- Monitor and troubleshoot issues through Amazon CloudWatch Logs.

---

## 8. Expected Outcomes

### Technical Improvements

- Process thousands of concurrent ticket booking requests.
- Eliminate ticket overbooking.
- Automatically scale based on incoming traffic.
- Significantly reduce operational costs.

### Long-term Value

- Provide a complete AWS Serverless reference architecture for learning and research.
- Serve as a foundation for a real-world online ticket booking platform.
- Be easily extended with additional features such as online payment integration, event management, and analytics dashboards in the future.