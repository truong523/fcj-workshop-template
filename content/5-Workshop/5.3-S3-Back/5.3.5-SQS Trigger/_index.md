---
title : "Connect Amazon SQS to AWS Lambda"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b>5.3.5.</b> "
---

#### Configure an Amazon SQS Trigger for AWS Lambda

After creating the Amazon SQS queue and assigning the required IAM permissions to AWS Lambda, the next step is to configure an **Amazon SQS Trigger**. This trigger automatically invokes the Lambda function whenever a new message is added to the queue.

The trigger serves as the connection between **Amazon SQS** and **AWS Lambda**. Each ticket booking request sent to the queue is automatically processed by the Lambda function without requiring any manual intervention.

Follow these steps to configure the trigger:

- Open the **AWS Management Console** and navigate to **AWS Lambda**.
- Select the Lambda function created earlier, for example **flashsale-ticket-worker**.
- In the **Function overview** section, click **+ Add trigger**.

Configure the trigger with the following settings:

- **Select a source:** Choose **Amazon SQS**.
- **SQS Queue:** Select the **flashsale-booking-queue** created in the previous step.
- **Batch size:** Set the value to **1** so that Lambda processes one message at a time. This helps reduce concurrent database updates and minimizes the risk of **Overbooking**.

After completing the configuration, scroll to the bottom of the page and click **Add** to create the trigger.

Once the trigger has been successfully created, Amazon SQS will automatically invoke the AWS Lambda function whenever a new message arrives in the queue. This asynchronous processing model improves system scalability, enables efficient request handling, and helps maintain system stability during high-demand Flash Sale events.

![trigger-success](/images/5-Workshop/5.3-S3-vpc/trigger.jpg)