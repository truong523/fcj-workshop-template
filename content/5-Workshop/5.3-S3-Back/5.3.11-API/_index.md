---
title : "System Stress Testing"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b>5.3.11.</b> "
---

#### System Stress Testing

After deploying all components of the Serverless architecture, the next step is to evaluate the system's performance under heavy load. The purpose of this test is to verify that **Amazon SQS**, **AWS Lambda**, and the **PostgreSQL row-level locking mechanism (`SELECT ... FOR UPDATE`)** can correctly process a large number of concurrent ticket booking requests without causing **overbooking**.

During the test, use a load-testing tool such as **Apache JMeter**, **K6**, or a custom **Node.js** or **Python** script to simulate approximately **1,000 concurrent ticket booking requests**.

Perform the following steps:

- Prepare a load-testing tool such as **Apache JMeter**, **K6**, or a custom **Node.js/Python** application.
- Configure the tool to send approximately **1,000 concurrent requests**.
- Send ticket booking requests to **Amazon API Gateway** or directly to **Amazon SQS**.
- Monitor the execution of **AWS Lambda** using **Amazon CloudWatch Logs**.
- Verify the data stored in **Amazon RDS PostgreSQL** after the test is completed.

Assume that the **tickets** table initially contains **10 available tickets (stock = 10)**. After the stress test, the system is considered successful if the following conditions are met:

- The remaining ticket **stock** is **0**.
- Exactly **10 successful booking records** exist in the **bookings** table.
- All remaining requests are rejected because the tickets are sold out.
- No **overbooking** or duplicate booking records are generated.

An example of the test result is shown below:

![stress-result](/images/5-Workshop/5.3-S3-vpc/11.2.jpg)

This stress test demonstrates the scalability and reliability of the **AWS Serverless Event-Driven** architecture. It also verifies that **Amazon SQS**, **AWS Lambda**, and **Amazon RDS PostgreSQL** work together correctly to process concurrent requests while preventing data inconsistency and overbooking during high-traffic events.