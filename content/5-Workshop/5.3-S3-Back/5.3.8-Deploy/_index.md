---
title : "Deploying Source Code to AWS Lambda"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b>5.3.8.</b> "
---

#### Deploying Source Code to AWS Lambda

After packaging the application into the **deploy.zip** file, the next step is to upload the package to **AWS Lambda**. AWS Lambda supports direct deployment from ZIP archives, allowing developers to quickly update the function code without managing any servers.

Perform the following steps:

- Open the **AWS Management Console** and navigate to **AWS Lambda**.
- Select the **flashsale-ticket-worker** function created in the previous steps.
- Open the **Code** tab.
- Click **Upload from** and choose **.zip file**.
- Select the **deploy.zip** file from your local project directory.
- Click **Save** to upload and deploy the source code.

After the upload is complete, AWS Lambda automatically updates the function with the new version of the source code. You can verify the deployment by viewing the **index.js** file directly in the AWS Lambda code editor.

![lambda-code](/images/5-Workshop/5.3-S3-vpc/8.jpg)

Once the deployment is successful, AWS Lambda is ready to receive messages from **Amazon SQS** and execute the ticket booking business logic as part of the designed **AWS Serverless Event-Driven** architecture.