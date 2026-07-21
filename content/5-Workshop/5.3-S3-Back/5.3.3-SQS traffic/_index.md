---
title : "Configure Amazon SQS"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3.3.</b> "
---

#### Configure Amazon SQS

Amazon Simple Queue Service (Amazon SQS) is a fully managed message queuing service provided by Amazon Web Services (AWS). In the Event Ticket Booking System, Amazon SQS acts as a message queue to temporarily store ticket booking requests before they are processed by AWS Lambda.

Amazon SQS is used to decouple the request processing workflow from the web application. Instead of processing booking requests immediately, all requests are placed into a queue and handled sequentially by AWS Lambda. This approach improves system scalability, prevents server overload, and ensures reliable request processing during high-traffic events such as Flash Sales.

The deployment steps are as follows:

- Access the **AWS Management Console**, search for **Amazon SQS**, and select **Simple Queue Service**.
- Verify that the selected AWS Region is **Asia Pacific (Singapore) – ap-southeast-1**.
- Click **Create queue** to create a new queue.

Next, configure the queue settings as follows:

- **Type:** Select **Standard**.
- **Queue Name:** Enter `flashsale-booking-queue`.
- **Visibility Timeout:** Set the value to **30 Seconds** to prevent multiple Lambda functions from processing the same message simultaneously.
- **Delivery Delay:** Keep the default value of **0 Seconds**.
- **Receive Message Wait Time:** Set the value to **20 Seconds** to enable **Long Polling**, reducing unnecessary polling requests and lowering operational costs.
- **Message Retention Period:** Keep the default value of **4 Days**.

![sqs-setting](/images/5-Workshop/5.3-S3-vpc/sqs-setting.png)

After completing the configuration, scroll to the bottom of the page and click **Create queue** to create the Amazon SQS queue.

Once the queue has been created successfully, it will be ready to receive ticket booking requests from Amazon API Gateway and forward them to AWS Lambda for asynchronous processing.

![sqs-created](/images/5-Workshop/5.3-S3-vpc/sqs-created.png)