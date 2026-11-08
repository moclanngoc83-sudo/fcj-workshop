---
title: "Triển khai ứng dụng bằng AWS CodeDeploy"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

#### **Bước 1: Chuẩn bị EC2 Instance**

1. Đăng nhập vào **AWS Management Console**.
2. Mở **Amazon EC2 Console**.
3. Chọn **Instances** và chọn Instance sẽ được sử dụng để chạy ứng dụng Spring Boot.
4. Kiểm tra để đảm bảo Instance đang ở trạng thái **Running**.
5. Ghi lại Instance ID để kiểm tra trong các bước tiếp theo.

EC2 Instance cần có IAM Instance Profile phù hợp, quyền truy cập mạng đến các dịch vụ AWS cần thiết và **CodeDeploy Agent** đã được cài đặt cũng như đang chạy.

#### **Bước 2: Tạo IAM Service Role cho CodeDeploy**

1. Mở **IAM Console**.
2. Chọn **Roles**, sau đó nhấn **Create role**.
3. Chọn **AWS service** làm loại thực thể đáng tin cậy (Trusted entity type).
4. Chọn **CodeDeploy** làm trường hợp sử dụng (Use case).
5. Gắn các quyền dịch vụ CodeDeploy phù hợp.
6. Nhập tên Role:

   `CodeDeployServiceRole`

7. Chọn **Create role**.

Sử dụng Role vừa tạo cho CodeDeploy khi cấu hình Deployment Group.

#### **Bước 3: Tạo CodeDeploy Application**

1. Mở **AWS CodeDeploy Console**.
2. Trong thanh điều hướng, chọn **Applications**.
3. Nhấn **Create application**.
4. Nhập tên Application:

   `cicd-aws-demo-app`

5. Tại mục **Compute platform**, chọn **EC2/On-premises**.
6. Nhấn **Create application**.

#### **Bước 4: Tạo Deployment Group**

1. Mở Application `cicd-aws-demo-app`.
2. Chọn **Create deployment group**.
3. Nhập tên Deployment Group:

   `cicd-aws-demo-deployment-group`

4. Trong mục **Service role**, chọn `CodeDeployServiceRole`.
5. Trong mục **Deployment type**, chọn phương thức triển khai phù hợp với workshop.
6. Trong mục **Environment configuration**, chọn **Amazon EC2 instances**.
7. Cấu hình tiêu chí lựa chọn Instance bằng EC2 Tags, đảm bảo máy chủ ứng dụng cần triển khai được chọn chính xác.
8. Lưu Deployment Group.

{{% notice warning %}}
Kiểm tra kỹ EC2 Tags và cấu hình Deployment Group trước khi triển khai. Việc chọn nhầm Instance có thể khiến ứng dụng được triển khai lên những máy chủ không mong muốn.
{{% /notice %}}

#### **Bước 5: Chuẩn bị các tệp triển khai ứng dụng**

Mở thư mục dự án trên máy tính:

```powershell
cd D:\cicd-aws-demo
```

Kiểm tra xem dự án có các tệp cấu hình và tập lệnh triển khai hay không:

```powershell
dir
dir scripts
```

Dự án cần có:

- **`appspec.yml`** — định nghĩa các tệp cần triển khai và các Lifecycle Hooks.
- **`scripts/`** — chứa các tập lệnh được sử dụng trong quá trình triển khai.
- **`pom.xml`** — định nghĩa cấu hình Build của Maven.

Kiểm tra để đảm bảo đường dẫn và tên tệp trong `appspec.yml` khớp với các tệp thực tế trong dự án. Các tập lệnh triển khai cũng phải có quyền thực thi phù hợp và sử dụng những lệnh tương thích với hệ điều hành của EC2 Instance đích.

#### **Bước 6: Triển khai ứng dụng**

Sau khi Artifact của ứng dụng được tạo bởi **AWS CodeBuild** và sẵn sàng để CodeDeploy sử dụng:

1. Mở **AWS CodeDeploy Console**.
2. Chọn Application `cicd-aws-demo-app`.
3. Mở Deployment Group `cicd-aws-demo-deployment-group`.
4. Chọn **Create deployment**.
5. Chọn nguồn Revision đã được cấu hình và cung cấp vị trí Artifact cùng thông tin Revision theo yêu cầu của cấu hình triển khai.
6. Bắt đầu quá trình triển khai.

Nếu dự án được điều phối bởi **AWS CodePipeline**, Pipeline có thể tự động kích hoạt giai đoạn triển khai này. Trong trường hợp đó, hãy sử dụng CodePipeline để chạy toàn bộ quy trình thay vì tạo một lần triển khai riêng theo cách thủ công.

#### **Bước 7: Kiểm tra trạng thái triển khai**

1. Mở thông tin chi tiết của lần triển khai trong **CodeDeploy Console**.
2. Kiểm tra các sự kiện triển khai (Deployment Events).
3. Xác nhận trạng thái triển khai là **Succeeded**.
4. Nếu triển khai thất bại, hãy xác định Lifecycle Event xảy ra lỗi và kiểm tra nhật ký (Logs) tương ứng trên EC2 Instance.

Một số nguyên nhân phổ biến bao gồm CodeDeploy Agent chưa được cài đặt, quyền IAM không chính xác, tệp `appspec.yml` không hợp lệ, thiếu tập lệnh triển khai hoặc ứng dụng không thể khởi động.

#### **Bước 8: Kiểm tra ứng dụng Web**

Sau khi triển khai thành công, kiểm tra ứng dụng bằng địa chỉ Public của EC2 Instance hoặc Endpoint tương ứng của ứng dụng.

Ví dụ:

`http://<EC2-Public-IP>:8080`

Thay `<EC2-Public-IP>` bằng địa chỉ IP Public thực tế của Instance. Ví dụ này giả định ứng dụng đang lắng nghe trên cổng **8080** và Instance đã được cấu hình để chấp nhận lưu lượng truy cập kiểm thử.

Nếu trang web phản hồi như mong đợi, ứng dụng đã chạy trên EC2 Instance.

#### **Tổng kết**

Trong phần này, bạn đã cấu hình **AWS CodeDeploy**, tạo Deployment Group và triển khai Artifact của ứng dụng lên **Amazon EC2**.

Bước tiếp theo là tích hợp các giai đoạn Source, Build và Deploy vào **AWS CodePipeline**, giúp ứng dụng được triển khai tự động mỗi khi phát hiện có thay đổi trong mã nguồn.