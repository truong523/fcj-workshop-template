---
title : "Testing the Amazon SQS Processing Workflow"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b>5.3.10.</b> "
---

#### Testing the Amazon SQS Processing Workflow

After configuring **Amazon SQS**, **AWS Lambda**, and the required **IAM permissions**, the next step is to verify the complete processing workflow. The objective is to confirm that whenever a message is sent to the Amazon SQS queue, AWS Lambda is automatically triggered to process the ticket booking request.

Perform the following steps:

- Open the **AWS Management Console** and navigate to **Amazon SQS**.
- Select the **flashsale-booking-queue** created in the previous steps.
- Click **Send and receive messages**.
- In the **Message body** field, enter the following JSON message:

```json
{
  "ticketId": 1,
  "userId": 999
}
```

- Click **Send message** to submit the message to the queue.

Once the message is successfully sent, **Amazon SQS** automatically triggers **AWS Lambda** through the configured trigger.

Next, open **AWS Lambda**, select the **flashsale-ticket-worker** function, navigate to the **Monitor** tab, and click **View CloudWatch logs** to verify the execution result.

If the CloudWatch Logs display a message similar to:

```text
[SUCCESS] User 999 successfully booked ticket 1
```

you can conclude that the integration between **Amazon SQS**, **AWS Lambda**, **Amazon RDS PostgreSQL**, and **AWS Secrets Manager** is working correctly.

This verification confirms that the **AWS Serverless Event-Driven** architecture for the Flash Sale Ticket Booking System has been successfully deployed and is functioning as expected.

![lambda-code](/images/5-Workshop/5.3-S3-vpc/10.jpg)