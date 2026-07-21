---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Tìm hiểu cách ủy quyền truy cập Billing and Cost Management Console cho IAM User.
* Thực hành Identity Federation với AWS IAM Identity Center để quản lý truy cập tập trung.
* Tìm hiểu IAM Permission Boundaries nhằm giới hạn quyền tối đa của người dùng.
* Thực hành quản lý quyền truy cập và dọn dẹp tài nguyên AWS sau khi hoàn thành bài lab.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Billing Console Delegation <br> - Tạo IAM User và IAM Group <br> - Bật IAM Access cho Billing Console | 22/06/2026 | 22/06/2026 | <https://000007.awsstudygroup.com/> |
| 3 | - Tạo IAM Policy BillingViewAccess <br> - Gán Policy cho IAM User <br> - Kiểm tra quyền truy cập Billing Console | 23/06/2026 | 23/06/2026 | <https://000007.awsstudygroup.com/> |
| 4 | - Tạo AWS Organizations <br> - Tạo các Member Accounts và Organizational Units (OUs) <br> - Thực hành Switch Role giữa các AWS Accounts | 24/06/2026 | 24/06/2026 | <https://000007.awsstudygroup.com/> |
| 5 | - Cấu hình AWS CLI với IAM Identity Center <br> - Thực hành Time-based Access Control <br> - Tìm hiểu Customer Managed Policies và Identity Store APIs | 25/06/2026 | 25/06/2026 | <https://000007.awsstudygroup.com/> |
| 6 | - Tạo IAM Permission Boundary <br> - Kiểm tra giới hạn quyền EC2 theo Region <br> - Dọn dẹp toàn bộ tài nguyên AWS | 26/06/2026 | 26/06/2026 | <https://000007.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:

* Hiểu được cơ chế **Billing Console Delegation**, cho phép IAM User truy cập Billing and Cost Management Console mà không cần sử dụng tài khoản Root.

* Tạo thành công IAM User, IAM Group và IAM Policy **BillingViewAccess**, đồng thời kiểm tra quyền truy cập Billing Console.

* Triển khai AWS Organizations với nhiều Member Accounts và Organizational Units (OUs) để quản lý tập trung các tài khoản AWS.

* Thực hiện thành công **Switch Role** giữa Management Account và Member Accounts thông qua AWS IAM Identity Center.

* Cấu hình AWS CLI với AWS IAM Identity Center bằng cả hai phương thức **Manual** và **Automatic (AWS SSO)**.

* Áp dụng **Time-based Access Control** bằng Permission Set và IAM Conditions để giới hạn thời gian truy cập.

* Tìm hiểu và sử dụng **Customer Managed Policies (CMP)** cùng **Identity Store APIs** để quản lý người dùng và nhóm trong AWS IAM Identity Center.

* Tạo và áp dụng **IAM Permission Boundary** để giới hạn quyền tối đa của IAM User.

* Kiểm tra thành công chính sách giới hạn Region:
  * Amazon EC2 được phép hoạt động tại **ap-southeast-1 (Singapore)**.
  * Amazon EC2 bị từ chối truy cập tại các Region khác mặc dù người dùng được gán **AmazonEC2FullAccess**.

* Hoàn thành việc dọn dẹp toàn bộ IAM Users, IAM Groups, IAM Policies, IAM Identity Center và các tài nguyên AWS sau khi kết thúc bài thực hành.

* Nắm vững cách kết hợp **Billing Console Delegation**, **AWS IAM Identity Center** và **IAM Permission Boundaries** để triển khai mô hình quản lý truy cập tập trung, bảo mật và tuân thủ nguyên tắc **Least Privilege** trên AWS.