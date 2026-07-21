---
title : "Uploading Source Code to AWS Lambda"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b>5.3.9.</b> "
---

#### Uploading Source Code to AWS Lambda

After preparing and packaging the application into the **deploy.zip** file, the next step is to upload the deployment package to **AWS Lambda**. AWS Lambda supports direct deployment from ZIP files, making it easy to update the function code without managing any server infrastructure.

Perform the following steps:

- Open the **AWS Management Console** and navigate to **AWS Lambda**.
- Select the **flashsale-ticket-worker** function created in the previous steps.
- Open the **Code** tab.
- Click **Upload from** and choose **.zip file**.
- Select the **deploy.zip** file from your local project directory.
- Click **Save** to begin uploading and deploying the source code.

After the upload is complete, AWS Lambda automatically updates the function with the latest version of the application. You can verify the deployment by opening the **index.js** file in the Lambda code editor.

![lambda-code](/images/5-Workshop/5.3-S3-vpc/8.jpg)

Once the source code has been successfully deployed, AWS Lambda is ready to receive messages from **Amazon SQS**, connect securely to **Amazon RDS PostgreSQL**, and execute the ticket booking workflow based on the **AWS Serverless Event-Driven** architecture.