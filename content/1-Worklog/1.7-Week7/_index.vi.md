---
title: "Nhật ký thực tập tuần 7"
date: 2026-10-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7

* Tìm hiểu các tài nguyên AWS cần thiết để triển khai ứng dụng web Spring Boot.
* Học cách chuẩn bị một máy chủ Amazon EC2 phục vụ việc triển khai ứng dụng.
* Tìm hiểu về Security Group, Key Pair và kết nối SSH để truy cập EC2.
* Tìm hiểu về IAM Role và các quyền cần thiết đối với những dịch vụ triển khai của AWS.
* Chuẩn bị môi trường triển khai cho bước cấu hình AWS CodeDeploy tiếp theo.

### Các công việc cần thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|-----| --- | --- | --- | --- |
| 1 | - Xem xét lại kiến trúc của dự án CI/CD và xác định các tài nguyên AWS cần thiết cho quá trình triển khai. <br> - Tìm hiểu vai trò của Amazon EC2 trong việc cung cấp môi trường lưu trữ và chạy ứng dụng. | 10/03/2026 | 10/03/2026 | [Tài liệu Amazon EC2](https://docs.aws.amazon.com/ec2/) |
| 2 | - Tìm hiểu các loại EC2 Instance, Amazon Machine Image (AMI) và các tùy chọn lưu trữ. <br> - Xác định hệ điều hành và cấu hình máy chủ phù hợp cho ứng dụng demo. | 10/04/2026 | 10/04/2026 | [Các loại EC2 Instance](https://docs.aws.amazon.com/ec2/latest/instancetypes/instance-types.html) |
| 3 | - Tìm hiểu cách cấu hình Security Group của EC2 để kiểm soát lưu lượng mạng đi vào và đi ra. <br> - Tìm hiểu cách truy cập SSH và cổng mạng cần thiết cho ứng dụng Spring Boot. | 10/05/2026 | 10/05/2026 | [EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) |
| 4 | - Tìm hiểu về IAM Role và IAM Policy dành cho EC2 và các dịch vụ triển khai của AWS. <br> - Tìm hiểu các quyền cần thiết để EC2 có thể giao tiếp với những dịch vụ AWS và nhận hướng dẫn triển khai ứng dụng. | 10/06/2026 | 10/07/2026 | [IAM Roles for EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) |
| 5 | - Chuẩn bị hoặc kiểm tra lại môi trường triển khai trên EC2. <br> - Kiểm tra quyền truy cập hệ điều hành, các thành phần phụ thuộc cần thiết và quyền truy cập thư mục ứng dụng. <br> - Tìm hiểu các điều kiện cần thiết trước khi cài đặt CodeDeploy Agent. | 10/08/2026 | 10/09/2026 | [CodeDeploy Agent](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html) |

### Kết quả đạt được trong tuần 7

* Xác định được các tài nguyên AWS cần thiết để lưu trữ và triển khai ứng dụng web Spring Boot.
* Hiểu được các tùy chọn cấu hình EC2 cơ bản, bao gồm loại Instance, AMI và dung lượng lưu trữ.
* Nắm được cách Security Group kiểm soát lưu lượng mạng truy cập vào máy chủ EC2.
* Hiểu được mục đích của IAM Role và các quyền trong việc cho phép những dịch vụ AWS giao tiếp với nhau một cách an toàn.
* Xác định được các yêu cầu về môi trường để chạy ứng dụng trên EC2.
* Hoàn thiện kế hoạch chuẩn bị môi trường triển khai cho giai đoạn tiếp theo: cấu hình AWS CodeDeploy.