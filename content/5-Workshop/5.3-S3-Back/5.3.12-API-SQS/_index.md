---
title : "Retrieving Configuration Information from AWS"
date : 2024-01-01
weight : 12
chapter : false
pre : " <b>5.3.12.</b> "
---

#### Retrieving Configuration Information from AWS

After deploying the required AWS services, the next step is to retrieve the configuration information needed by the application. Two important values are required: the **Amazon RDS Endpoint** and the **Secret Name** stored in **AWS Secrets Manager**.

Perform the following steps:

##### Retrieve the Amazon RDS Endpoint

- Open the **AWS Management Console** and navigate to **Amazon RDS**.
- Select **Databases** from the left navigation menu.
- Choose the database created earlier, for example **flashsale-ticket-db**.
- Open the **Connectivity & security** tab.
- Copy the value displayed in the **Endpoint** field.

This endpoint is the database address that the application uses to connect to the **Amazon RDS PostgreSQL** instance.

##### Retrieve the Secret Name

- Open **AWS Secrets Manager**.
- Select the secret that was automatically created when the Amazon RDS database was provisioned.
- On the **Secret details** page, copy the value of **Secret name**.

AWS Lambda will use this secret to securely retrieve the database username and password at runtime without hardcoding sensitive credentials in the source code.

![secret-name](/images/5-Workshop/5.3-S3-vpc/12.jpg)

After obtaining the **Amazon RDS Endpoint** and **Secret Name**, save both values. They will be used in the next step to configure the application and establish a secure connection between **AWS Lambda** and **Amazon RDS PostgreSQL** through **AWS Secrets Manager**.