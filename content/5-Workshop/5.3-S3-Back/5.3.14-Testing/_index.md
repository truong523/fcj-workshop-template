---
title : "Opening AWS CloudShell"
date : 2024-01-01
weight : 14
chapter : false
pre : " <b>5.3.14.</b> "
---

#### Opening AWS CloudShell

After configuring **AWS Lambda**, the next step is to open **AWS CloudShell** to execute command-line operations directly within the AWS environment. AWS CloudShell is a browser-based terminal integrated into the **AWS Management Console**, providing a preconfigured **AWS CLI** environment without requiring any local installation.

Perform the following steps:

- Open the **AWS Management Console**.
- On the top navigation bar, locate the **CloudShell** icon (the Terminal `>_` icon) near the **Notifications** icon.
- Click the **CloudShell** icon to launch the command-line environment.
- Wait approximately **20 to 30 seconds** while AWS provisions the CloudShell session.
- Once the initialization is complete, a terminal window will appear at the bottom of the page and will be ready to accept **AWS CLI** commands.

After CloudShell has started successfully, the terminal displays information about the currently authenticated AWS account. From this environment, you can manage AWS resources, execute AWS CLI commands, and perform administrative tasks without installing the AWS CLI on your local computer.

Using **AWS CloudShell** simplifies AWS infrastructure management by providing a secure, browser-based terminal with the AWS CLI already configured using your current AWS credentials.
