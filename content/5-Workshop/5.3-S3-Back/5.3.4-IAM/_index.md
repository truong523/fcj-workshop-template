---
title : "Configure IAM"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.3.4.</b> "
---

#### Configure IAM for AWS Lambda

**AWS Identity and Access Management (IAM)** is an AWS service that enables you to securely manage identities and control access to AWS resources. In the **Flash Sale Ticket Booking System**, IAM is used to grant the AWS Lambda function permission to access required AWS services such as **Amazon SQS**, **Amazon RDS**, and **AWS Secrets Manager**.

After creating the AWS Lambda function, the next step is to grant it the required permissions to read and process messages from **Amazon SQS**. These permissions should follow the **Principle of Least Privilege**, ensuring that the function receives only the permissions necessary to perform its tasks.

Follow these steps to configure the IAM role:

- Open the **AWS Management Console** and navigate to **AWS Lambda**.
- Select the **flashsale-ticket-node** function.
- Open the **Configuration** tab.
- In the left navigation pane, choose **Permissions**.
- Under **Execution role**, click the IAM Role link that AWS automatically created for the Lambda function.

Next, attach the required IAM policy:

- Click **Add permissions**.
- Select **Attach policies**.
- Search for the **AWSLambdaSQSQueueExecutionRole** policy.
- Select the policy.
- Click **Add permissions** to attach it to the IAM Role.

The **AWSLambdaSQSQueueExecutionRole** policy allows the Lambda function to perform essential Amazon SQS operations, including receiving messages, deleting messages after successful processing, and writing execution logs to **Amazon CloudWatch**.

After completing the configuration, the Lambda execution role has the required permissions to access **Amazon SQS** and is ready for the next step of connecting the SQS queue to the Lambda function.

![iam-role](/images/5-Workshop/5.3-S3-vpc/iam.jpg)