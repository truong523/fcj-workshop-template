---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Tìm hiểu cách kiểm soát quyền truy cập Amazon EC2 bằng AWS IAM và Resource Tags.
* Thực hành tạo IAM User, IAM Group, IAM Role và IAM Policy với các điều kiện (Conditions).
* Kiểm tra quyền truy cập EC2 dựa trên Region và Resource Tags.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu IAM Conditions và Resource Tags <br> - Tạo IAM User và IAM Group <br> - Bật xác thực đa yếu tố (MFA) cho IAM User | 08/06/2026 | 08/06/2026 | <https://000007.awsstudygroup.com/> |
| 3 | - Tạo IAM Policies <br> - Cấu hình điều kiện giới hạn theo Region <br> - Cấu hình điều kiện dựa trên Resource Tags | 09/06/2026 | 09/06/2026 | <https://000007.awsstudygroup.com/> |
| 4 | - Tạo IAM Role <br> - Cấu hình Trust Relationship <br> - Gán IAM Policies cho IAM Role | 10/06/2026 | 10/06/2026 | <https://000007.awsstudygroup.com/> |
| 5 | - Thực hành Switch Role <br> - Kiểm tra quyền truy cập EC2 theo Region <br> - Tạo Amazon EC2 Instance với Resource Tags | 11/06/2026 | 11/06/2026 | <https://000007.awsstudygroup.com/> |
| 6 | - Chỉnh sửa Resource Tags <br> - Kiểm tra quyền Terminate EC2 <br> - Dọn dẹp tài nguyên AWS | 12/06/2026 | 12/06/2026 | <https://000007.awsstudygroup.com/> |

### Kết quả đạt được tuần 6:

* Hiểu được cách sử dụng AWS Identity and Access Management (IAM) kết hợp với Resource Tags để kiểm soát quyền truy cập vào Amazon EC2.

* Tạo thành công IAM User, IAM Group, IAM Role và IAM Policies nhằm triển khai mô hình phân quyền trên AWS.

* Xây dựng và áp dụng các IAM Policies với nhiều điều kiện khác nhau, bao gồm:
  * Giới hạn theo AWS Region.
  * Điều kiện `ec2:CreateAction`.
  * Điều kiện `aws:RequestTag`.
  * Điều kiện `aws:TagKeys`.
  * Điều kiện `ec2:ResourceTag`.

* Cấu hình IAM Role với Trust Relationship yêu cầu xác thực đa yếu tố (MFA) trước khi thực hiện Assume Role.

* Thực hiện thành công Switch Role từ IAM User sang IAM Role và xác minh các quyền được cấp.

* Kiểm tra chính sách giới hạn truy cập theo Region:
  * Region **Asia Pacific (Tokyo)** bị từ chối truy cập.
  * Region **US East (N. Virginia)** được phép truy cập theo chính sách IAM.

* Kiểm tra việc tạo Amazon EC2 Instance bằng Resource Tags:
  * EC2 có Tag **Team=Alpha** được phép tạo.
  * EC2 có Tag **Team=Beta** bị từ chối theo IAM Policy đã cấu hình.

* Kiểm tra quyền chỉnh sửa Resource Tags và quyền Terminate Amazon EC2 theo đúng các điều kiện trong IAM Policy.

* Hoàn thành việc dọn dẹp toàn bộ IAM Users, IAM Groups, IAM Roles, IAM Policies và Amazon EC2 Instances sau khi kết thúc bài thực hành.

* Nắm vững cách kết hợp IAM Policies, IAM Conditions và Resource Tags để triển khai mô hình **Least Privilege Access Control**, góp phần nâng cao tính bảo mật và kiểm soát truy cập trên AWS.