---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Tìm hiểu AWS Identity and Access Management (IAM) và cơ chế phân quyền.
* Thực hành tạo IAM User, IAM Group, IAM Role và Assume Role.
* Áp dụng IAM Conditions để tăng cường bảo mật và kiểm soát quyền truy cập.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu IAM (User, Group, Role, Policy) <br> - Tìm hiểu Request đến AWS Service <br> - Quy trình Assume Role | 01/06/2026 | 01/06/2026 | <https://000007.awsstudygroup.com/> |
| 3 | - Tạo IAM Group <br> - Tạo 4 IAM User với các quyền khác nhau <br> - Gán Policy và Group cho User | 02/06/2026 | 02/06/2026 | <https://000007.awsstudygroup.com/> |
| 4 | - Kiểm tra quyền của từng IAM User <br> - Tạo IAM Role có quyền Administrator <br> - Cấu hình Trust Relationship | 03/06/2026 | 03/06/2026 | <https://000007.awsstudygroup.com/> |
| 5 | - Thực hành Switch Role <br> - Cấu hình Condition giới hạn theo địa chỉ IP <br> - Kiểm tra Assume Role | 04/06/2026 | 04/06/2026 | <https://000007.awsstudygroup.com/> |
| 6 | - Cấu hình Condition giới hạn theo thời gian <br> - Kiểm tra quyền truy cập <br> - Dọn dẹp tài nguyên IAM | 05/06/2026 | 05/06/2026 | <https://000007.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* Hiểu được các khái niệm cốt lõi của AWS IAM gồm User, Group, Role, Policy và cơ chế xử lý Request.

* Nắm được quy trình Assume Role thông qua AWS Security Token Service (STS) và sử dụng Switch Role để chuyển đổi quyền truy cập.

* Tạo thành công IAM Group và 4 IAM User với các mức quyền khác nhau theo yêu cầu.

* Tạo IAM Role có quyền AdministratorAccess và cấu hình Trust Relationship cho phép User không có quyền thực hiện Assume Role.

* Áp dụng thành công IAM Conditions để giới hạn Switch Role theo địa chỉ IP và thời gian truy cập.

* Kiểm tra và xác nhận quyền truy cập của từng IAM User theo đúng chính sách đã cấu hình.

* Thực hiện dọn dẹp toàn bộ IAM Users, IAM Group và IAM Role sau khi hoàn thành bài thực hành.

* Hiểu được nguyên tắc **Least Privilege** và cách tăng cường bảo mật hệ thống bằng **Context-based Access Control** trong AWS IAM.