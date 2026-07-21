---
title : "Create AWS Lambda"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.3.2.</b> "
---

#### Create an AWS Lambda Function (Worker)

AWS Lambda is a **serverless computing** service provided by Amazon Web Services (AWS) that allows you to run code without provisioning or managing servers. In the **Flash Sale Ticket Booking System**, AWS Lambda acts as the worker responsible for processing ticket booking requests after they are placed into **Amazon SQS**.

After deploying **Amazon RDS PostgreSQL**, the next step is to create a Lambda function that will handle ticket booking requests. The Lambda function will be configured to run inside the same **Virtual Private Cloud (VPC)** as the Amazon RDS instance, allowing it to securely connect to the database.

Follow these steps to create the Lambda function:

- Open the **AWS Management Console**, search for **AWS Lambda**, and choose **Create function**.
- Select **Author from scratch**.
- Set the **Function name** to `flashsale-ticket-node`.
- Under **Runtime**, choose **Node.js 20.x**.
- Keep the **Architecture** as **x86_64**.

Next, configure the execution permissions:

- In the **Permissions** section, choose **Change default execution role**.
- Select **Create a new role with basic Lambda permissions**.
- AWS will automatically create a default IAM Role that grants permission to write logs to **Amazon CloudWatch**. Additional permissions for **Amazon SQS**, **Amazon RDS**, and **AWS Secrets Manager** will be added later following the **Principle of Least Privilege**.

In the **Advanced settings**, configure the network connection as follows:

- **Enable VPC:** Enable VPC access for the Lambda function.
- **Virtual Private Cloud (VPC):** Select the **Default VPC**.
- **Subnets:** Select all available subnets within the VPC.
- **Security Groups:** Choose the default Security Group or the Security Group created specifically for this project.

Configuring the Lambda function inside the VPC allows it to communicate securely with **Amazon RDS PostgreSQL**, since the database is configured with **Public access = No** and only accepts connections from resources within the same private network.

After completing the configuration, click **Create function**. Once the function status changes to **Active**, the Lambda function is ready to be connected to **Amazon SQS** and begin processing ticket booking requests.

![lambda-vpc](/images/5-Workshop/5.3-S3-vpc/lambda.jpg)