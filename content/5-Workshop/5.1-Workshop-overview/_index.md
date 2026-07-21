---
title : "Introduction"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to the Event Ticket Booking System

In this workshop, we build a **Limited Event Ticket Booking System** on **Amazon Web Services (AWS)** using a **Serverless architecture** to address the challenge of handling a large number of ticket booking requests within a short period of time.

The system leverages AWS services to automatically scale resources, improve system performance, and ensure that ticket booking requests are processed accurately and securely.

**Project Objectives:**

+ Build an online ticket booking system capable of handling thousands of concurrent user requests.
+ Use **Amazon SQS** to queue booking requests and prevent system overload.
+ Use **AWS Lambda** together with **PostgreSQL transactions** and **FOR UPDATE** to prevent ticket overbooking.
+ Enhance system security through **IAM**, **AWS Secrets Manager**, and **Amazon CloudFront**.
+ Utilize a **Serverless architecture** to reduce deployment and operational costs.

#### Workshop Overview

In this workshop, the entire system is deployed on **Amazon Web Services (AWS)** using a **Serverless Event-Driven Architecture**. Each AWS service is responsible for a specific task to ensure scalability, high availability, and optimal system performance.

The overall system architecture consists of the following AWS services:

+ **Amazon CloudFront** 
+ **AWS WAF** 
+ **AWS Amplify Hosting** 
+ **Amazon Cognito**
+ **Amazon API Gateway**
+ **Amazon SQS** 
+ **AWS Lambda** 
+ **Amazon RDS PostgreSQL** 
+ **Amazon SES** 
+ **Amazon CloudWatch** 
+ **IAM**, **AWS Secrets Manager**, **AWS CloudTrail**, **AWS X-Ray**, **AWS Budgets**, and **AWS CloudFormation** 

The system is designed to efficiently handle a large number of requests during Flash Sale events, minimize system congestion, and ensure that every ticket is sold only within the available inventory.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram.jpg)