---
title: "Đẩy mã nguồn lên GitHub"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.3.2. </b> "
---

#### **1. Kiểm tra các tệp của dự án**

Trước khi tải mã nguồn lên GitHub, hãy đảm bảo rằng **dự án Spring Boot** của bạn được lưu trong thư mục `D:\cicd-aws-demo`.

Dự án cần có các tệp và thư mục sau:

```text
cicd-aws-demo/
├── src/
├── pom.xml
├── buildspec.yml
├── appspec.yml
└── scripts/
```

Thư mục `src/` chứa mã nguồn ứng dụng và các bài kiểm thử đơn vị (Unit Test). Tệp `pom.xml` định nghĩa dự án Maven và các thư viện phụ thuộc.

#### **2. Mở Terminal của dự án**

Mở **PowerShell** hoặc Terminal trong **VS Code** và di chuyển đến thư mục dự án:

```powershell
cd D:\cicd-aws-demo
```

Kiểm tra trạng thái Git hiện tại:

```powershell
git status
```

Nếu dự án đã được kết nối với GitHub, lệnh này sẽ hiển thị nhánh hiện tại và những thay đổi chưa được commit.

#### **3. Kiểm tra kho lưu trữ từ xa trên GitHub**

Kiểm tra kho lưu trữ từ xa (Remote Repository) đã được cấu hình cho dự án:

```powershell
git remote -v
```

URL của repository dự kiến là:

`https://github.com/moclanngoc83-sudo/cicd-aws-demo.git`

Nếu repository từ xa đã được cấu hình chính xác, bạn không cần thêm lại.

Nếu URL của repository không chính xác, hãy cập nhật bằng lệnh:

```powershell
git remote set-url origin https://github.com/moclanngoc83-sudo/cicd-aws-demo.git
```

Nếu chưa tồn tại remote có tên `origin`, hãy thêm bằng lệnh:

```powershell
git remote add origin https://github.com/moclanngoc83-sudo/cicd-aws-demo.git
```

#### **4. Commit mã nguồn**

Thêm các tệp của dự án vào vùng chờ (Staging Area) của Git:

```powershell
git add .
```

Commit các thay đổi:

```powershell
git commit -m "Prepare Spring Boot application for CI/CD"
```

Nếu Git thông báo không có gì để commit, có thể các tệp hiện tại đã được commit trước đó.

Nếu Git yêu cầu cấu hình thông tin người dùng, hãy thiết lập tên và địa chỉ email của bạn:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Thay các giá trị ví dụ bằng tên và email Git thực tế của bạn, sau đó thực hiện lại lệnh commit nếu cần.

#### **5. Đẩy mã nguồn lên GitHub**

Kiểm tra nhánh hiện tại:

```powershell
git branch
```

Nếu nhánh hiện tại có tên là `main`, hãy đẩy mã nguồn lên GitHub bằng lệnh:

```powershell
git push -u origin main
```

Nếu nhánh hiện tại có tên khác, hãy thay `main` bằng tên nhánh thực tế.

Nếu Git yêu cầu xác thực, hãy hoàn tất quá trình xác thực bằng phương thức được hỗ trợ trong cấu hình GitHub của bạn.

#### **6. Kiểm tra repository trên GitHub**

Mở repository sau trên trình duyệt để kiểm tra:

[https://github.com/moclanngoc83-sudo/cicd-aws-demo](https://github.com/moclanngoc83-sudo/cicd-aws-demo)