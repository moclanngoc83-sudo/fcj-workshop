---
title: "Triển khai và kiểm tra ứng dụng"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.5.2. </b> "
---

## Bước 1: Chuẩn bị các tệp triển khai

AWS CodeDeploy cần một bản sửa đổi ứng dụng (Application Revision) chứa các tệp cần triển khai và tệp `appspec.yml` mô tả các hướng dẫn triển khai.

Trong thư mục dự án, kiểm tra xem các tệp triển khai đã tồn tại hay chưa:

```text
cicd-aws-demo/
├── appspec.yml
├── buildspec.yml
├── pom.xml
├── scripts/
│   ├── install_dependencies.sh
│   ├── start_server.sh
│   └── stop_server.sh
└── src/
```

Tên tệp và cấu trúc thư mục trong Revision phải khớp với các đường dẫn được chỉ định trong `appspec.yml`.

Đối với triển khai trên EC2, tệp AppSpec phải có tên `appspec.yml` và được đặt tại thư mục gốc của Revision triển khai.

## Bước 2: Build ứng dụng

Thực hiện Build và kiểm thử ứng dụng Spring Boot trước khi triển khai.

Tại thư mục dự án, chạy lệnh:

```powershell
.\mvnw.cmd clean test package
```

Kiểm tra kết quả Build. Maven cần hoàn tất thành công và tệp JAR của ứng dụng phải được tạo trong thư mục `target/`.

Ví dụ:

```powershell
Get-ChildItem .\target\*.jar
```

Nếu các bài kiểm thử thất bại hoặc tệp JAR không được tạo, hãy khắc phục vấn đề trước khi tiếp tục.

## Bước 3: Bắt đầu triển khai

Có hai cách để bắt đầu quá trình triển khai.

### Phương án A: Triển khai thông qua CodePipeline

Sử dụng phương án này khi dự án đã được kết nối với AWS CodePipeline.

1. Mở **AWS CodePipeline**.
2. Chọn Pipeline đã được cấu hình cho dự án `cicd-aws-demo`.
3. Chọn **Release change** nếu Pipeline không tự động được kích hoạt.
4. Chờ các giai đoạn Source, Build và Deploy thực thi.
5. Mở giai đoạn Deploy để kiểm tra trạng thái.

Giai đoạn triển khai cần sử dụng CodeDeploy Application `cicd-aws-demo-app` và Deployment Group `cicd-aws-demo-deployment-group`.

### Phương án B: Tạo một lần triển khai thủ công

Sử dụng phương án này để kiểm tra CodeDeploy trước khi kết nối với CodePipeline.

1. Mở **AWS CodeDeploy**.
2. Chọn **Applications** và mở `cicd-aws-demo-app`.
3. Chọn Deployment Group `cicd-aws-demo-deployment-group`.
4. Chọn **Create deployment**.
5. Chọn nguồn Revision phù hợp.

   Đối với Revision lưu trên S3, hãy chọn S3 Bucket, Object Key và Version hoặc ETag theo yêu cầu. Revision được tải lên phải chứa tệp `appspec.yml` tại thư mục gốc.

6. Chọn **Create deployment**.
7. Chờ quá trình triển khai hoàn tất.

Quá trình triển khai thủ công yêu cầu một Revision đã được đóng gói và tải lên nguồn lưu trữ đã chọn. Chỉ Build tệp JAR trên máy tính cục bộ không đồng nghĩa với việc đã tạo được Revision triển khai trên S3.

## Bước 4: Kiểm tra trạng thái triển khai

Trong CodeDeploy, mở thông tin chi tiết của lần triển khai và kiểm tra trạng thái.

- **Succeeded:** Các giai đoạn trong vòng đời triển khai đã hoàn tất thành công.
- **Failed:** Mở thông tin chi tiết của lần triển khai và kiểm tra Lifecycle Event bị lỗi.
- **In Progress:** Chờ quá trình triển khai hoàn tất trước khi kiểm tra ứng dụng.

Kiểm tra các Lifecycle Event để xác định lỗi xảy ra trong giai đoạn DownloadBundle, Install, ApplicationStart hoặc một Deployment Hook khác.

## Bước 5: Kiểm tra ứng dụng trên EC2

Kết nối đến EC2 Instance và kiểm tra tiến trình ứng dụng cũng như nhật ký hoạt động (Logs).

Đối với Instance chạy Linux, có thể sử dụng các lệnh sau:

```bash
ps -ef | grep java
```

```bash
sudo journalctl -u codedeploy-agent --no-pager -n 100
```

Nếu ứng dụng ghi nhật ký vào tệp, hãy kiểm tra Application Log tại đường dẫn lưu trữ đã được cấu hình.

Nếu quá trình triển khai thành công nhưng ứng dụng không phản hồi, hãy kiểm tra các yếu tố sau:

- Tiến trình Spring Boot có đang chạy hay không.
- Ứng dụng có đang lắng nghe trên đúng cổng được cấu hình hay không.
- Security Group của EC2 có cho phép lưu lượng truy cập đến cổng đó hay không.
- Các tập lệnh triển khai có sử dụng đúng đường dẫn tệp và có quyền thực thi phù hợp hay không.

## Bước 6: Kiểm tra ứng dụng Web

Nếu ứng dụng Spring Boot được cấu hình để lắng nghe trên cổng `8080`, hãy mở địa chỉ sau trong trình duyệt:

```text
http://<EC2-Public-IP>:8080
```

Thay `<EC2-Public-IP>` bằng địa chỉ IPv4 Public thực tế của EC2 Instance.

Nếu ứng dụng sử dụng cổng khác hoặc một Endpoint cụ thể, hãy sử dụng đúng cổng và Endpoint đã được cấu hình.

Nếu trang web không tải được, hãy kiểm tra trạng thái hoạt động của ứng dụng ngay trên EC2 Instance, đồng thời kiểm tra Security Group và cấu hình mạng của EC2.

## Bước 7: Ghi nhận kết quả

Ghi lại các thông tin sau để đưa vào báo cáo dự án:

| Hạng mục | Kết quả mong đợi |
|---|---|
| CodeDeploy Application | `cicd-aws-demo-app` đã tồn tại |
| Deployment Group | `cicd-aws-demo-deployment-group` đã tồn tại |
| Trạng thái triển khai | `Succeeded` |
| Tiến trình ứng dụng | Đang chạy trên EC2 |
| Kiểm tra truy cập Web | Ứng dụng phản hồi tại địa chỉ đã cấu hình |

Chụp ảnh màn hình trạng thái triển khai, các Lifecycle Event và kết quả kiểm tra thành công trên trình duyệt để làm minh chứng cho báo cáo tốt nghiệp.

## Xử lý sự cố

| Vấn đề | Nội dung cần kiểm tra |
|---|---|
| Triển khai thất bại trước khi cài đặt | Nguồn Revision, quyền IAM và vị trí của tệp `appspec.yml` |
| EC2 Instance không được chọn | Tags của Instance và tiêu chí lựa chọn trong Deployment Group |
| CodeDeploy Agent không khả dụng | Việc cài đặt Agent, trạng thái dịch vụ và kết nối mạng |
| Ứng dụng không thể khởi động | Quyền thực thi của Script, đường dẫn tệp, phiên bản Java và Application Logs |
| Trình duyệt không thể kết nối | Cổng ứng dụng, trạng thái tiến trình và Security Group của EC2 |

## Kết quả

Ứng dụng đã được triển khai lên EC2 và được kiểm tra thông qua trạng thái triển khai, kiểm tra trên Instance và truy cập bằng trình duyệt.

Sau khi triển khai thủ công thành công, có thể sử dụng cùng Application và Deployment Group để AWS CodePipeline thực hiện quá trình triển khai tự động.