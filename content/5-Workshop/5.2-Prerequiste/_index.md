---
title : "Architecture"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.2.</b> "
---

#### Overall System Architecture

The system is built using a **Serverless Event-Driven Architecture** on **Amazon Web Services (AWS)**. This architecture separates the process of receiving user requests from the ticket booking business logic, allowing the system to maintain stable performance even when a large number of users access it simultaneously.

According to the system architecture diagram, the workflow is as follows:

1. Users access the ticket booking website through a web browser.
2. All incoming traffic is distributed through **Amazon CloudFront**, while **AWS WAF** inspects and filters malicious requests to protect the system from common web attacks.
3. The frontend application is deployed on **AWS Amplify Hosting**, providing fast and reliable access for users.
4. Users sign in or register through **Amazon Cognito**. If additional authentication is required, the system uses **AWS Lambda Custom Authorizer**.
5. After successful authentication, ticket booking requests are sent to **Amazon API Gateway**.
6. API Gateway forwards all booking requests to the **Amazon SQS Booking Queue** for asynchronous processing, preventing the system from becoming overloaded when many users submit requests simultaneously.
7. **AWS Lambda** automatically retrieves messages from Amazon SQS and processes the ticket booking requests.
8. Lambda connects to **Amazon RDS PostgreSQL**, starts a database transaction using **SELECT ... FOR UPDATE**, verifies ticket availability, updates the remaining ticket quantity, and stores the booking information if the transaction is successful.
9. During operation, all processing logs are recorded in **Amazon CloudWatch**, while booking confirmation emails are sent to customers through **Amazon SES**.
10. In addition, services such as **IAM**, **AWS Secrets Manager**, **AWS CloudTrail**, **AWS X-Ray**, **AWS Budgets**, and **AWS CloudFormation** provide identity and access management, security, monitoring, performance analysis, cost management, and infrastructure deployment.

This architecture enables the system to scale automatically, handle high traffic efficiently, reduce operational costs, and maintain stability during Flash Sale events with a large number of concurrent users.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram.jpg)

**Figure 5.1. Overall Architecture of the Limited Event Ticket Booking System on AWS**

#### AWS Services Used

To build the Flash Sale Ticket system, the project utilizes multiple **Amazon Web Services (AWS)**. Each service is responsible for a specific function within the overall system.

| **AWS Service** | **Role in the System** |
|-----------------|------------------------|
| **Amazon CloudFront** | Delivers website content and accelerates user access. |
| **AWS WAF** | Protects the system against common web attacks such as SQL Injection, XSS, and basic DDoS attacks. |
| **AWS Amplify Hosting** | Deploys and hosts the frontend application. |
| **Amazon Cognito** | Manages user accounts and authentication. |
| **Amazon API Gateway** | Receives ticket booking requests from clients through REST APIs. |
| **Amazon SQS** | Stores booking requests in a message queue for sequential processing. |
| **AWS Lambda** | Executes the ticket booking business logic using a serverless computing model. |
| **Amazon RDS PostgreSQL** | Stores user information, ticket data, and booking history. |
| **Amazon SES** | Sends booking confirmation emails to customers. |
| **Amazon CloudWatch** | Monitors logs, system performance, and application health. |
| **AWS X-Ray** | Traces requests and analyzes application performance. |
| **AWS IAM** | Manages access permissions between AWS services. |
| **AWS Secrets Manager** | Securely stores database credentials and sensitive information. |
| **AWS CloudTrail** | Records AWS account activities for auditing purposes. |
| **AWS Budgets** | Monitors AWS costs and sends budget alerts. |
| **AWS CloudFormation** | Automates infrastructure deployment using Infrastructure as Code (IaC). |