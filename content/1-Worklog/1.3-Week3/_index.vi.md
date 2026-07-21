---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Tìm hiểu kiến trúc mạng trên AWS với Amazon VPC.
* Triển khai Amazon RDS trong Private Subnet.
* Kết nối EC2 với RDS, thực hiện Backup, Restore và dọn dẹp tài nguyên.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tạo Amazon VPC <br> - Cấu hình Public Subnet và Private Subnet <br> - Tạo Internet Gateway và Route Table | 18/05/2026 | 18/05/2026 | <https://000007.awsstudygroup.com/> |
| 3 | - Cấu hình Auto-assign Public IP <br> - Tạo Security Group cho EC2 và Amazon RDS <br> - Áp dụng nguyên tắc tối thiểu quyền | 19/05/2026 | 19/05/2026 | <https://000007.awsstudygroup.com/> |
| 4 | - Tạo DB Subnet Group <br> - Khởi tạo Amazon EC2 Instance <br> - Cài đặt MySQL Client và kết nối SSH | 20/05/2026 | 20/05/2026 | <https://000007.awsstudygroup.com/> |
| 5 | - Tạo Amazon RDS (MySQL) <br> - Cấu hình DB Subnet Group <br> - Kết nối EC2 với Amazon RDS <br> - Tạo Database và Table | 21/05/2026 | 21/05/2026 | <https://000007.awsstudygroup.com/> |
| 6 | - Tạo Manual Snapshot <br> - Restore RDS từ Snapshot <br> - Kiểm tra dữ liệu <br> - Dọn dẹp tài nguyên AWS | 22/05/2026 | 22/05/2026 | <https://000007.awsstudygroup.com/> |

### Kết quả đạt được tuần 3:

* Hiểu được cách xây dựng kiến trúc mạng trên AWS bằng Amazon VPC.

* Tạo thành công VPC với Public Subnet và Private Subnet, đồng thời cấu hình Internet Gateway và Route Table.

* Cấu hình Security Group cho EC2 và Amazon RDS theo nguyên tắc bảo mật tối thiểu.

* Tạo thành công DB Subnet Group và triển khai Amazon RDS (MySQL) trong Private Subnet.

* Kết nối thành công từ Amazon EC2 đến Amazon RDS thông qua MySQL Client.

* Thực hiện tạo cơ sở dữ liệu, bảng và thêm dữ liệu vào Amazon RDS.

* Tạo Manual Snapshot và Restore thành công một Amazon RDS Instance mới, đảm bảo dữ liệu được bảo toàn.

* Hoàn thành việc dọn dẹp toàn bộ tài nguyên AWS sau khi kết thúc bài thực hành, tránh phát sinh chi phí không cần thiết.