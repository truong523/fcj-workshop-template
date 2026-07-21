---
title : "Performing Stress Testing with a Bash Script"
date : 2024-01-01
weight : 15
chapter : false
pre : " <b>5.3.15.</b> "
---

#### Performing Stress Testing with a Bash Script

After completing the system configuration, the next step is to evaluate the scalability of the Serverless architecture by sending a large number of messages to **Amazon SQS**. **AWS CloudShell** comes with the **AWS CLI** pre-installed and automatically uses the permissions of the currently authenticated AWS account. Therefore, no additional software or custom Node.js application is required to perform the stress test.

Perform the following steps:

- Open **AWS CloudShell** from the **AWS Management Console**.
- In the terminal window, copy and paste the following **Bash script**, which sends multiple messages to the Amazon SQS queue.
- Press **Enter** to execute the script.
- Monitor the output. Each successful request returns a **MessageId**, confirming that the message has been successfully added to the Amazon SQS queue.

Example Bash script:

```bash
for i in {1..1000}
do
  aws sqs send-message \
    --queue-url https://sqs.ap-southeast-1.amazonaws.com/ACCOUNT_ID/flashsale-booking-queue \
    --message-body "{\"ticketId\":1,\"userId\":$i}"
done
```

> **Note:** Replace `ACCOUNT_ID` with your AWS account ID and use the correct **Queue URL** of your Amazon SQS queue.

![cloudshell-stress-test](/images/5-Workshop/5.3-S3-vpc/15.1.jpg)

![cloudshell-stress-test](/images/5-Workshop/5.3-S3-vpc/15.2.jpg)

After the Bash script finishes executing, **Amazon SQS** will contain a large number of queued messages, automatically triggering multiple **AWS Lambda** invocations to process ticket booking requests. This stress test verifies the system's ability to handle high volumes of concurrent requests and demonstrates the scalability of the **AWS Serverless Event-Driven** architecture.