---
title : "Configure Amazon RDS"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.3.1</b> "
---

#### Initialize Amazon RDS PostgreSQL

Amazon Relational Database Service (Amazon RDS) is a managed relational database service provided by Amazon Web Services (AWS). In the Event Ticket Booking System, Amazon RDS uses **PostgreSQL** to store user information, ticket data, and booking history.

Amazon RDS is deployed first because it requires a relatively long initialization time, typically **10 to 15 minutes**. Creating the database first allows the remaining deployment time to be used for configuring other AWS services such as Amazon SQS, AWS Lambda, and IAM, thereby reducing the overall deployment time.

The deployment steps are as follows:

- Access the **AWS Management Console**, search for **Amazon RDS**, and choose **Create database**.
- Under **Database creation method**, select **Standard Create**.
- Under **Engine options**, choose **PostgreSQL** as the database engine.
- Under **Templates**, select **Free Tier** to minimize deployment and testing costs.

Next, configure the basic database settings:

- **DB Instance Identifier:** Specify a database name, for example, `flashsale-ticket-db`.
- **Master Username:** Configure the administrator account for the database.
- **Master Password:** Create a strong password and save it securely, as it will be required later when configuring AWS Secrets Manager.

![setting](/images/5-Workshop/5.3-S3-vpc/setting.png)

Under the **Connectivity** section, configure the following settings:

- **Virtual Private Cloud (VPC):** Select the **Default VPC**.
- **Public Access:** Select **No** to prevent direct access to the database from the Internet.
- **VPC Security Group:** Select **Create new** and specify a security group name.

After completing all the configurations, click **Create database** to start provisioning the Amazon RDS instance. Once the database status changes to **Available**, it is ready to be connected with the other AWS services in the system.

![endpoint](/images/5-Workshop/5.3-S3-vpc/tlm.png)