---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Tìm hiểu Amazon EBS Provisioned IOPS (io2) và công nghệ NVMe.
* Triển khai chia sẻ dữ liệu an toàn giữa các EC2 Instance thông qua NFS.
* Thực hành quản lý EBS Volume và dọn dẹp tài nguyên AWS.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Chuẩn bị 2 Amazon EC2 Instance trong cùng VPC <br> - Cài đặt NFS Utilities <br> - Cấu hình Security Group cho NFS | 25/05/2026 | 25/05/2026 | <https://000007.awsstudygroup.com/> |
| 3 | - Tạo Amazon EBS Volume (io2) <br> - Cấu hình Provisioned IOPS <br> - Gắn EBS Volume vào EC2 Server | 26/05/2026 | 26/05/2026 | <https://000007.awsstudygroup.com/> |
| 4 | - Định dạng EBS Volume <br> - Mount File System <br> - Kiểm tra thiết bị NVMe | 27/05/2026 | 27/05/2026 | <https://000007.awsstudygroup.com/> |
| 5 | - Cấu hình NFS Server <br> - Chia sẻ thư mục qua NFS <br> - Mở cổng 2049 trên Security Group | 28/05/2026 | 28/05/2026 | <https://000007.awsstudygroup.com/> |
| 6 | - Kết nối EC2 Client đến NFS Server <br> - Kiểm tra đọc/ghi dữ liệu <br> - Dọn dẹp tài nguyên AWS | 29/05/2026 | 29/05/2026 | <https://000007.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

* Hiểu được cách hoạt động của Amazon EBS Provisioned IOPS (io2) và công nghệ NVMe.

* Tạo thành công Amazon EBS Volume với Provisioned IOPS và gắn vào EC2 Instance.

* Định dạng và mount thành công EBS Volume để sử dụng làm thư mục chia sẻ.

* Cấu hình thành công NFS Server trên EC2 và chia sẻ dữ liệu an toàn trong cùng VPC.

* Kết nối thành công từ EC2 Client đến NFS Server và thực hiện đọc, ghi dữ liệu trên thư mục dùng chung.

* Hiểu được cách triển khai lưu trữ chia sẻ trong AWS mà không cần truyền dữ liệu qua Internet.

* Hoàn thành việc dọn dẹp toàn bộ tài nguyên AWS sau khi kết thúc bài thực hành nhằm tránh phát sinh chi phí.

* Hoàn thành toàn bộ mục tiêu đề ra trong tuần và nắm được quy trình triển khai lưu trữ chia sẻ bằng Amazon EBS kết hợp NFS.