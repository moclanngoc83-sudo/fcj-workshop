---
title: "Chuẩn bị ứng dụng Spring Boot"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.3.1. </b> "
---

#### **1. Kiểm tra môi trường phát triển**

Trước khi xây dựng ứng dụng web, hãy đảm bảo rằng **Java 17**, **Git** và **Maven** đã được cài đặt trên máy tính của bạn.

Mở **PowerShell** hoặc Terminal trong **VS Code** và chạy các lệnh sau:

```powershell
java -version
git --version
```

Để kiểm tra xem dự án có bao gồm Maven Wrapper hay không, hãy di chuyển đến thư mục dự án và chạy:

```powershell
.\mvnw.cmd -version
```

Nếu dự án không có tệp `mvnw.cmd`, hãy cài đặt Maven hoặc cấu hình dự án để sử dụng phiên bản Maven đã được cài đặt trên máy tính.

#### **2. Mở dự án**

Mở dự án **cicd-aws-demo** hiện có bằng **VS Code**.

Dự án cần có các tệp và thư mục chính sau:

```text
cicd-aws-demo/
├── src/
│   ├── main/
│   │   └── java/
│   └── test/
│       └── java/
├── pom.xml
├── buildspec.yml
├── appspec.yml
└── scripts/
```

- **`src/main/java/`** chứa mã nguồn của ứng dụng.
- **`src/test/java/`** chứa các bài kiểm thử đơn vị (Unit Test).
- **`pom.xml`** định nghĩa dự án Maven và các thư viện phụ thuộc.
- **`buildspec.yml`** chứa các hướng dẫn xây dựng ứng dụng cho AWS CodeBuild.
- **`appspec.yml`** định nghĩa các hướng dẫn triển khai ứng dụng cho AWS CodeDeploy.
- **`scripts/`** chứa các tập lệnh triển khai.

#### **3. Xây dựng ứng dụng Web**

Trong Terminal của VS Code, di chuyển đến thư mục gốc của dự án:

```powershell
cd "D:\cicd-aws-demo"
```

Nếu dự án của bạn được lưu ở vị trí khác, hãy thay thế đường dẫn trên bằng đường dẫn thực tế đến thư mục dự án.

Chạy lệnh sau để xây dựng ứng dụng và thực thi các bài kiểm thử đơn vị:

```powershell
.\mvnw.cmd clean package
```

Nếu quá trình xây dựng thành công, Maven sẽ tạo gói ứng dụng trong thư mục **`target/`**.

Tìm tệp **`.jar`** được tạo trong thư mục đó.

#### **4. Chạy ứng dụng trên máy cục bộ**

Chạy ứng dụng Spring Boot bằng tệp JAR vừa được tạo:

```powershell
java -jar target/<application-name>.jar
```

Thay **`<application-name>.jar`** bằng tên tệp JAR thực tế được tạo trong thư mục `target/`.

Mở trình duyệt và truy cập địa chỉ cục bộ của ứng dụng, thông thường là:

`http://localhost:8080`

Nếu ứng dụng khởi động thành công và trang web phản hồi như mong đợi, ứng dụng đã sẵn sàng cho bước tiếp theo.

#### **5. Kết quả mong đợi**

Sau khi hoàn thành phần này, bạn cần có:

- Một **ứng dụng web Spring Boot** hoạt động bình thường.
- Quá trình **Maven Build** trên máy cục bộ hoàn tất thành công.
- Các bài kiểm thử đơn vị được thực thi trong quá trình Build.
- Một gói ứng dụng JAR được tạo trong thư mục **`target/`**.

#### **Nội dung tiếp theo**

- [Đẩy mã nguồn lên GitHub](../5.3.2-push-to-github/)