---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b>5.</b> "
---

# Building a Flash Sale Ticket Booking System on AWS Serverless

#### Overview

In this workshop, we will build a **Flash Sale Ticket Booking System** using an **AWS Serverless Event-Driven Architecture**.

The system is designed to process a large number of ticket booking requests within a short period while preventing **Race Conditions** and **Overbooking**. Instead of processing requests directly on a server, user requests are placed into **Amazon SQS**, where **AWS Lambda** consumes and processes them sequentially before updating ticket information in **Amazon RDS PostgreSQL**.

The solution also integrates **Amazon API Gateway** to receive booking requests from the website, **AWS Secrets Manager** to securely store database credentials, **Amazon SES** to send booking confirmation emails, and **Amazon CloudWatch** to monitor system activities and logs.

Throughout this workshop, you will learn how to deploy a complete **AWS Serverless Event-Driven** application, including the backend, frontend, API integration, and system testing.

#### Contents

1. [System Overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequisite/)
3. [Deploying the Serverless Backend](5.3-Backend-serverless/)
4. [Deploying the Frontend Website](5.4-Frontend/)
5. [System Evaluation](5.5-Evaluation/)