---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b>1.11.</b> "
---

### Week 11 Objectives

* Design the Serverless architecture for the Event Ticket Booking System.
* Deploy and configure core AWS services.
* Establish communication between Amazon API Gateway, Amazon SQS, AWS Lambda, and Amazon RDS.

### Tasks

| Day | Task | Start Date | Finish Date | Reference |
| --- | --- | --- | --- | --- |
| Mon | Study the overall Serverless architecture and identify required AWS services | 13/07/2026 | 13/07/2026 | https://aws.amazon.com/ |
| Tue | Create and configure Amazon RDS PostgreSQL database | 14/07/2026 | 14/07/2026 | https://docs.aws.amazon.com/rds/ |
| Wed | Create AWS Lambda function and configure IAM permissions | 15/07/2026 | 15/07/2026 | https://docs.aws.amazon.com/lambda/ |
| Thu | Create Amazon SQS queue and configure Lambda Trigger | 16/07/2026 | 16/07/2026 | https://docs.aws.amazon.com/sqs/ |
| Fri | Configure API Gateway and integrate it with Amazon SQS | 17/07/2026 | 17/07/2026 | https://docs.aws.amazon.com/apigateway/ |

### Week 11 Results

* Successfully designed the Serverless architecture for the Event Ticket Booking System.
* Created an Amazon RDS PostgreSQL database.
* Deployed the AWS Lambda function using Node.js.
* Configured IAM Roles and Policies following the Principle of Least Privilege.
* Created an Amazon SQS queue to process ticket booking requests asynchronously.
* Configured Lambda Trigger to automatically process messages from Amazon SQS.
* Created a REST API using Amazon API Gateway and connected it with Amazon SQS.
* Verified communication among API Gateway, SQS, Lambda, and RDS.