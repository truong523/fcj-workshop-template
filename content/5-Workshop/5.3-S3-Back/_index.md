---
title : "Serverless Backend"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3.</b> "
---

#### Overview

In this section, you will deploy the **Serverless Backend** for the **Flash Sale Ticket Booking System** on **Amazon Web Services (AWS)**. The Serverless architecture enables the system to process ticket booking requests without managing servers while automatically scaling to handle increasing numbers of users.

The backend is built using the following core AWS services:

- **AWS Lambda**: Executes the ticket booking business logic in a serverless environment.
- **Amazon SQS**: Receives and stores ticket booking requests in a queue, enabling asynchronous processing and preventing system overload during periods of high traffic.
- **AWS IAM**: Manages permissions between AWS services following the **Principle of Least Privilege** to enhance security.
- **AWS Secrets Manager**: Securely stores database credentials, eliminating the need to hardcode sensitive information in the application source code.
- **Amazon RDS PostgreSQL**: Stores user information, ticket data, and booking records.
- **Amazon CloudWatch**: Collects logs and monitors the overall performance and execution of the system.

In this chapter, you will learn how to create an **AWS Lambda** function, configure **Amazon SQS**, assign the required **IAM** permissions, securely manage database credentials with **AWS Secrets Manager**, and configure the **Amazon SQS trigger** for AWS Lambda to build a complete Serverless backend for the ticket booking system.