---
title : "Updating Configuration Information in AWS Lambda"
date : 2024-01-01
weight : 13
chapter : false
pre : " <b>5.3.13.</b> "
---

#### Updating Configuration Information in AWS Lambda

After obtaining the **Amazon RDS Endpoint** and **Secret Name** from AWS, the next step is to update these values in the **AWS Lambda** source code. Configuring these parameters correctly allows Lambda to connect to **Amazon RDS PostgreSQL** and securely retrieve database credentials from **AWS Secrets Manager** during execution.

Perform the following steps:

- Open the **AWS Management Console** and navigate to **AWS Lambda**.
- Select the **flashsale-ticket-worker** function.
- Open the **Code** tab and edit the **index.js** file.
- Locate the placeholder **YOUR_RDS_ENDPOINT_HERE** and replace it with the **Amazon RDS Endpoint** copied in the previous step.
- Locate the placeholder **YOUR_SECRET_NAME** and replace it with the **Secret Name** obtained from **AWS Secrets Manager**.
- After updating both values, click **Deploy** to save and deploy the latest version of the Lambda function.

Once the deployment is completed successfully, AWS Lambda displays the message **Successfully updated the function**, confirming that the source code has been updated and is ready to process ticket booking requests.

![lambda-update-config](/images/5-Workshop/5.3-S3-vpc/13.1.jpg)

![lambda-deploy-success](/images/5-Workshop/5.3-S3-vpc/13.2.jpg)

Updating the **Amazon RDS Endpoint** and **Secret Name** enables AWS Lambda to establish a secure connection to **Amazon RDS PostgreSQL** through **AWS Secrets Manager**. This approach eliminates the need to store sensitive database credentials directly in the source code, improving the overall security of the Serverless application.