---
title: "Cấu hình AWS CodeDeploy"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.5.1. </b> "
---

## Bước 1: Tạo IAM Role cho CodeDeploy

CodeDeploy cần có quyền truy cập các EC2 Instance và quản lý quá trình triển khai ứng dụng.

1. Đăng nhập vào [AWS Management Console](https://console.aws.amazon.com/).
2. Mở **IAM** và chọn **Roles**.
3. Chọn **Create role**.
4. Tại mục Trusted entity type, chọn **AWS service**.
5. Chọn **CodeDeploy** làm trường hợp sử dụng (Use case).
6. Chọn trường hợp sử dụng CodeDeploy dành cho triển khai trên EC2/on-premises.
7. Nhập tên Role:

   `CodeDeployServiceRole`

8. Tạo Role.

Sau khi tạo xong, mở Role và kiểm tra xem thực thể đáng tin cậy (Trusted entity) có cho phép dịch vụ CodeDeploy đảm nhận Role này hay không.

## Bước 2: Tạo CodeDeploy Application

1. Mở **AWS CodeDeploy** trong AWS Console.
2. Chọn **Applications** trong bảng điều hướng.
3. Chọn **Create application**.
4. Nhập các thông tin cấu hình sau:

    - **Application name:** `cicd-aws-demo-app`
    - **Compute platform:** `EC2/On-premises`

5. Chọn **Create application**.

Application vừa tạo sẽ xuất hiện trong danh sách ứng dụng của CodeDeploy.

## Bước 3: Tạo Deployment Group

1. Mở `cicd-aws-demo-app`.
2. Chọn **Create deployment group**.
3. Nhập các thông tin cấu hình sau:

    - **Deployment group name:** `cicd-aws-demo-deployment-group`
    - **Service role:** `CodeDeployServiceRole`
    - **Deployment type:** In-place (Triển khai tại chỗ)
    - **Environment configuration:** Amazon EC2 instances

4. Cấu hình tiêu chí lựa chọn EC2 Instance bằng Tags.

   Ví dụ: Nếu EC2 Instance có Tag `Name=ci-cd-demo-server`, hãy chọn các Instance khớp với Tag đó. Key và Value của Tag phải trùng khớp với thông tin thực tế của EC2 Instance.

5. Chọn **Create deployment group**.

**Quan trọng:** Deployment Group sẽ không triển khai lên một Instance nếu các tiêu chí lựa chọn không khớp với Instance đó. EC2 Instance cũng phải có IAM Instance Profile phù hợp và CodeDeploy Agent đã được cài đặt, đang chạy.

## Bước 4: Chuẩn bị EC2 Instance

Trước khi triển khai ứng dụng, hãy kiểm tra các điều kiện sau:

- EC2 Instance đang ở trạng thái Running.
- Instance có IAM Instance Profile cho phép truy cập các Artifact triển khai và dịch vụ cần thiết.
- CodeDeploy Agent đã được cài đặt và đang chạy.
- Instance có thể kết nối đến các AWS Endpoint cần thiết.
- Security Group của ứng dụng cho phép truy cập vào cổng mà ứng dụng web sử dụng.

Trên EC2 Instance chạy Linux, kiểm tra trạng thái Agent bằng lệnh:

```bash
sudo systemctl status codedeploy-agent
```

Nếu Agent đã được cài đặt nhưng đang dừng, hãy khởi động bằng lệnh:

```bash
sudo systemctl start codedeploy-agent
```

Nếu lệnh thông báo dịch vụ không tồn tại, hãy cài đặt CodeDeploy Agent phù hợp với hệ điều hành của Instance và AWS Region trước khi tiếp tục.

## Bước 5: Kiểm tra cấu hình

Trước khi chuyển sang bước triển khai, hãy kiểm tra các mục sau:

- Application `cicd-aws-demo-app` đã được tạo.
- Deployment Group `cicd-aws-demo-deployment-group` đã được tạo.
- Deployment Group nhắm đến đúng EC2 Instance cần triển khai.
- Service Role đã được lựa chọn chính xác.
- EC2 Instance có Instance Profile cần thiết.
- CodeDeploy Agent đang hoạt động.

Sau khi hoàn tất các bước kiểm tra này, hãy tiếp tục đến phần **Triển khai và kiểm tra ứng dụng (Deploy and Verify the Application)**.

## Kết quả

Sau khi hoàn thành phần này, CodeDeploy Application và Deployment Group đã được cấu hình và sẵn sàng tiếp nhận một lần triển khai từ AWS CodePipeline hoặc một lần triển khai được tạo thủ công.