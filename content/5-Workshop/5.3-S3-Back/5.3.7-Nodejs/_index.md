---
title : "Deploying AWS Lambda Source Code"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b>5.3.7.</b> "
---

#### Deploying AWS Lambda Source Code

After completing the configuration of the required AWS services, the next step is to deploy the ticket booking business logic to **AWS Lambda**. The application is developed using **Node.js** together with the **node-postgres (pg)** library to connect to and interact with the **Amazon RDS PostgreSQL** database.

Since the AWS Lambda runtime does not include the **pg** library by default, it must be installed locally before packaging and deploying the application.

Perform the following steps:

- Open **Command Prompt** or **Terminal** on your computer.
- Navigate to the Lambda project directory.
- Install the PostgreSQL client library by running the following command:

```bash
npm install pg
```

After the installation is complete, the project directory should contain the following files and folders:

- `node_modules`
- `package.json`
- `package-lock.json`

Next, create the Lambda source file:

- Open the project folder, for example:

```text
C:\Users\Acer\flashsale-worker
```

- Create a new file named **index.js**.
- Open **index.js** using Visual Studio Code or another text editor.
- Copy the ticket booking source code into **index.js** and save the file.

#### Packaging the Project

After completing the source code, package the project into a ZIP file for deployment.

> **Note:** Compress the **contents inside the project folder**, not the project folder itself.

Perform the following steps:

- Open the **flashsale-worker** project folder.
- Select all files and folders, including:

  - `index.js`
  - `node_modules`
  - `package.json`
  - `package-lock.json`

- Right-click and choose **Compress to ZIP file** or **Add to archive...** (ZIP format).
- Name the archive **deploy.zip**.

![zip-file](/images/5-Workshop/5.3-S3-vpc/deploy.jpg)

#### Uploading the Package to AWS Lambda

After creating the **deploy.zip** file, upload it to AWS Lambda.

Perform the following steps:

- Open **AWS Lambda** in the AWS Management Console.
- Select the **flashsale-ticket-worker** function.
- Open the **Code** tab.
- Choose **Upload from** → **.zip file**.
- Select the **deploy.zip** file.
- Click **Save** to complete the deployment.

Once the upload is successful, AWS Lambda will use the newly deployed source code for all subsequent executions.

![upload-code](/images/5-Workshop/5.3-S3-vpc/upload-code.png)