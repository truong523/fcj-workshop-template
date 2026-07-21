---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives

* Learn how to control access to Amazon EC2 using AWS IAM and Resource Tags.
* Practice creating IAM Users, IAM Roles, and IAM Policies with IAM Conditions.
* Verify Amazon EC2 access permissions based on AWS Regions and Resource Tags.

### Tasks for This Week

| Day | Tasks | Start Date | Completion Date | Reference |
| --- | --- | --- | --- | --- |
| Monday | - Learn IAM Conditions and Resource Tags <br> - Create IAM Users and IAM Groups <br> - Enable Multi-Factor Authentication (MFA) for IAM Users | 08/06/2026 | 08/06/2026 | <https://000007.awsstudygroup.com/> |
| Tuesday | - Create IAM Policies <br> - Configure Region-based Conditions <br> - Configure Resource Tag-based Conditions | 09/06/2026 | 09/06/2026 | <https://000007.awsstudygroup.com/> |
| Wednesday | - Create an IAM Role <br> - Configure Trust Relationships <br> - Attach IAM Policies to the IAM Role | 10/06/2026 | 10/06/2026 | <https://000007.awsstudygroup.com/> |
| Thursday | - Practice Switch Role <br> - Test Amazon EC2 access by Region <br> - Launch Amazon EC2 Instances with Resource Tags | 11/06/2026 | 11/06/2026 | <https://000007.awsstudygroup.com/> |
| Friday | - Modify Resource Tags <br> - Verify EC2 Termination Permissions <br> - Clean Up AWS Resources | 12/06/2026 | 12/06/2026 | <https://000007.awsstudygroup.com/> |

### Week 6 Achievements

* Gained a comprehensive understanding of access control for Amazon EC2 using AWS Identity and Access Management (IAM) together with Resource Tags.

* Successfully created IAM Users, IAM Groups, IAM Roles, and IAM Policies to implement role-based access control.

* Configured IAM Policies with advanced Conditions, including:
  * AWS Region restrictions
  * `ec2:CreateAction`
  * `aws:RequestTag`
  * `aws:TagKeys`
  * `ec2:ResourceTag`

* Configured an IAM Role with a Trust Relationship that requires Multi-Factor Authentication (MFA) before users can assume the role.

* Successfully performed Switch Role from an IAM User to an IAM Role and verified the assigned permissions.

* Tested Region-based access control:
  * Access to the **Asia Pacific (Tokyo)** Region was denied.
  * Access to the **US East (N. Virginia)** Region was allowed according to the IAM Policy.

* Verified Amazon EC2 instance creation using Resource Tags:
  * Instances tagged with **Team=Alpha** were successfully created.
  * Instances tagged with **Team=Beta** were denied according to the configured IAM Policy.

* Tested permissions for modifying Resource Tags and terminating Amazon EC2 instances based on IAM Conditions.

* Successfully cleaned up all AWS resources, including IAM Users, IAM Roles, IAM Policies, and Amazon EC2 instances after completing the hands-on lab.

* Gained practical experience in implementing the **Principle of Least Privilege** by combining IAM Policies, IAM Conditions, and Resource Tags to achieve secure and fine-grained access control in AWS.