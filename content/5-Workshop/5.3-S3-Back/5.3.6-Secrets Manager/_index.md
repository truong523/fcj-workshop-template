---
title : "Grant Access to AWS Secrets Manager"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b>5.3.6.</b> "
---

#### Grant AWS Lambda Access to AWS Secrets Manager

After creating the **Amazon RDS** database, the database credentials are securely stored in **AWS Secrets Manager**. To allow the AWS Lambda function to retrieve the database username, password, and connection information during execution, the Lambda execution role must be granted permission to access AWS Secrets Manager.

Follow these steps to grant the required permissions:

- Open the **AWS Management Console** and navigate to **AWS Lambda**.
- Select the Lambda function created earlier, for example **flashsale-ticket-worker**.
- Open the **Configuration** tab and choose **Permissions**.
- Under **Execution role**, click the Lambda IAM Role to open the IAM management page.

Next, attach the required IAM policy:

- Click **Add permissions**.
- Select **Attach policies**.
- In the search box, enter **SecretsManagerReadWrite**.
- Select the **SecretsManagerReadWrite** policy.
- Click **Add permissions** to attach the policy to the IAM Role.

After the policy has been successfully attached, the AWS Lambda function will be able to retrieve the Amazon RDS credentials stored in **AWS Secrets Manager** during request processing.

Using **AWS Secrets Manager** eliminates the need to hard-code database usernames and passwords in the application source code. This approach improves security and follows AWS best practices for securely managing sensitive credentials in Serverless applications.

![policy-success](/images/5-Workshop/5.3-S3-vpc/srm.jpg)