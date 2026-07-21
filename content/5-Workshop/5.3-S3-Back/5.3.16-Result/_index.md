---
title : "Configure Amazon API Gateway"
date : 2024-01-01
weight : 16
chapter : false
pre : " <b>5.3.16.</b> "
---

#### Configure Amazon API Gateway

After completing the backend implementation with **Amazon SQS** and **AWS Lambda**, the next step is to create a **REST API** using **Amazon API Gateway** to receive ticket booking requests from users. API Gateway accepts HTTP requests from the client application and sends the request directly to the Amazon SQS queue without requiring an intermediate Lambda function, improving performance and reducing operational costs.

Follow the steps below:

##### 1. Create a REST API

- Open the **AWS Management Console** and navigate to **Amazon API Gateway**.
- Click **Create API**.
- Under **REST API**, choose **Build**.
- Select **New API**.
- Enter **flashsale-api** as the API name.
- Click **Create API**.

---

##### 2. Create the `/buy` Resource

- Select **Actions** → **Create Resource**.
- Enter `buy` as the **Resource Name**.
- Click **Create Resource**.
- Select the newly created **/buy** resource.
- Choose **Actions** → **Create Method**.
- Select the **POST** method and click the **✓** icon to confirm.

---

##### 3. Configure Integration with Amazon SQS

In the **POST** method configuration, specify the following settings:

- **Integration type:** AWS Service
- **AWS Region:** `ap-southeast-1`
- **AWS Service:** Simple Queue Service (SQS)
- **HTTP Method:** POST
- **Action Type:** Use path override
- **Path Override:** `274118253697/flashsale-booking-queue`
- **Execution Role:** Enter the ARN of the IAM Role that has permission to access Amazon SQS.

---

##### 4. Configure the Mapping Template

To allow API Gateway to transform incoming JSON requests into the format required by Amazon SQS:

- Select **Integration Request**.
- Under **Mapping Templates**, click **Add mapping template**.
- For **Content-Type**, enter:

```text
application/json
```

- In the **Template Body**, enter the following:

```text
Action=SendMessage&MessageBody=$util.urlEncode($input.body)
```

- Click **Save** to apply the configuration.

---

##### 5. Deploy the API

After completing the configuration:

- Select **Actions** → **Deploy API**.
- Choose **[New Stage]**.
- Enter **prod** as the **Stage Name**.
- Click **Deploy**.

Once deployment is complete, API Gateway provides an **Invoke URL**, for example:

```text
https://xxxx.execute-api.ap-southeast-1.amazonaws.com/prod
```

This endpoint will be used by the client application to submit ticket booking requests.

![deploy-api](/images/5-Workshop/5.3-S3-vpc/16.jpg)

After the API has been successfully deployed, users can send HTTP **POST** requests to the `/buy` endpoint. Amazon API Gateway automatically transforms the request payload and forwards it to **Amazon SQS**. AWS Lambda then retrieves messages from the queue and processes ticket bookings according to the **Serverless Event-Driven Architecture** implemented for the system.