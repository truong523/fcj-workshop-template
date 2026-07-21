---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives

* Learn how to delegate access to the AWS Billing and Cost Management Console for IAM users.
* Practice identity federation using AWS IAM Identity Center for centralized access management.
* Learn how to use IAM Permission Boundaries to restrict the maximum permissions granted to IAM users.
* Practice AWS access management and clean up AWS resources after completing the hands-on lab.

### Tasks for This Week

| Day | Tasks | Start Date | Completion Date | Reference |
| --- | --- | --- | --- | --- |
| Monday | - Learn about Billing Console Delegation <br> - Create IAM Users and IAM Groups <br> - Enable IAM Access to the AWS Billing Console | 22/06/2026 | 22/06/2026 | <https://000007.awsstudygroup.com/> |
| Tuesday | - Create the BillingViewAccess IAM Policy <br> - Attach the policy to IAM Users <br> - Verify access to the AWS Billing Console | 23/06/2026 | 23/06/2026 | <https://000007.awsstudygroup.com/> |
| Wednesday | - Create an AWS Organization <br> - Create Member Accounts and Organizational Units (OUs) <br> - Practice switching roles between AWS accounts | 24/06/2026 | 24/06/2026 | <https://000007.awsstudygroup.com/> |
| Thursday | - Configure the AWS CLI with AWS IAM Identity Center <br> - Practice Time-based Access Control <br> - Learn about Customer Managed Policies and Identity Store APIs | 25/06/2026 | 25/06/2026 | <https://000007.awsstudygroup.com/> |
| Friday | - Create an IAM Permission Boundary <br> - Verify Amazon EC2 permission restrictions by AWS Region <br> - Clean up AWS resources | 26/06/2026 | 26/06/2026 | <https://000007.awsstudygroup.com/> |

### Week 8 Achievements

* Gained a solid understanding of **Billing Console Delegation**, allowing IAM users to access the AWS Billing and Cost Management Console without using the root account.

* Successfully created IAM Users, IAM Groups, and the **BillingViewAccess** IAM Policy, then verified user access to the Billing Console.

* Deployed **AWS Organizations** with multiple Member Accounts and Organizational Units (OUs) to centrally manage AWS accounts.

* Successfully performed **Switch Role** between the Management Account and Member Accounts using **AWS IAM Identity Center**.

* Configured the AWS CLI with AWS IAM Identity Center using both **Manual** and **Automatic (AWS SSO)** configuration methods.

* Implemented **Time-based Access Control** by configuring Permission Sets and IAM Conditions.

* Learned how to use **Customer Managed Policies (CMPs)** and **Identity Store APIs** to manage users and groups within AWS IAM Identity Center.

* Successfully created and applied an **IAM Permission Boundary** to define the maximum permissions available to IAM users.

* Verified Region-based access restrictions:
  * Amazon EC2 operations were allowed only in the **Asia Pacific (Singapore)** Region (`ap-southeast-1`).
  * Access to Amazon EC2 in other AWS Regions was denied even though the user was assigned the **AmazonEC2FullAccess** policy.

* Successfully cleaned up all AWS resources, including IAM Users, IAM Groups, IAM Policies, AWS IAM Identity Center configurations, and Amazon EC2 resources after completing the hands-on lab.

* Gained practical experience in combining **Billing Console Delegation**, **AWS IAM Identity Center**, and **IAM Permission Boundaries** to implement secure, centralized access management while following the **Principle of Least Privilege**.