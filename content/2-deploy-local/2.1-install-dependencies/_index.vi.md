+++
title = "Cài đặt các thành phần phụ thuộc"
date = 2024
weight = 3
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note%}}
Trong bài viết này, chúng ta sẽ thực hành trên máy tính Windows.
{{% /notice%}}

#### Cài đặt NodeJS
1. Truy cập [trang này](https://nodejs.org/en/download/current) để tải xuống Node.js **v25.8.1**
![note](/images/2-deploy-local/2.1/1.png)
2. Để hiểu rõ hơn, bạn nên làm theo video dưới đây để cài đặt NodeJS trên máy tính cá nhân.

{{< youtube 4FAtFwKVhn0 >}}

#### Cài đặt MySQL Community
1. Truy cập [trang này](https://mysql.com) để tải xuống MySQL Community **v8.0.45**
![note](/images/2-deploy-local/2.1/2.png)

2. Tương tự, hãy xem video này để cài đặt MySQL:

{{< youtube u96rVINbAUI >}}

Một số lưu ý khi cài đặt MySQL:

- Bạn nên cài đặt cả **MySQL Client** và **MySQL Server** để dễ dàng kiểm tra. Ngoài ra, hãy cài đặt **MySQL Workbench** và **MySQL Shell**, đây là hệ quản trị cơ sở dữ liệu tương tự như **Microsoft SQL Server Management Studio** dành cho Microsoft SQL Server. Bạn có thể cần chúng trong một số dự án tương lai.
- Trong MySQL, có hai loại người dùng: Root User và các người dùng khác, mỗi loại có các vai trò khác nhau. Hãy luôn ghi nhớ mật khẩu cho Root User và thêm một tài khoản mới khi cài đặt MySQL Server.
![note](/images/2-deploy-local/2.1/3.png)

#### Kết quả

Sau khi cài đặt NodeJS, npm cũng sẽ được bao gồm trong gói cài đặt. Kiểm tra xem NodeJS và npm đã được cài đặt thành công hay chưa bằng hai lệnh sau:

```bash
node -v
npm -v
```
![note](/images/2-deploy-local/2.1/4.png)

#### Sử dụng MySQL Shell

1. Tìm kiếm `MySQL Shell` trong thanh tìm kiếm của Windows, sau đó chọn `MySQL Shell`.

![note](/images/2-deploy-local/2.1/5.png)

2. Khi mở ra, bạn sẽ thấy giao diện như sau:

![note](/images/2-deploy-local/2.1/6.png)

3. Nhập `\sql` để chuyển chế độ nhập liệu (Input Mode) sang MySQL.

![note](/images/2-deploy-local/2.1/7.png)

4. Sau đó, kết nối tới MySQL Server bằng cách chạy lệnh: `\connect root@localhost`

![note](/images/2-deploy-local/2.1/8.png)

{{% notice note%}}
Nếu bạn không tạo người dùng trong quá trình cài đặt MySQL, bạn có thể kết nối tới MySQL Server bằng Root User. Trong trường hợp đó, **chuỗi kết nối (connection string)** sẽ là `root@localhost`, và đừng quên nhập mật khẩu Root User: `letmein12345` mà bạn đã thiết lập khi cài đặt.
{{% /notice%}}

5. Sử dụng lệnh `SHOW DATABASES;` để kiểm tra lại kết quả.

![note](/images/2-deploy-local/2.1/9.png)

6. **Vai trò của 4 database mặc định này:**

- **information_schema:** Lưu metadata về các bảng, cột, kiểu dữ liệu, quyền truy cập...
- **mysql:** Chứa thông tin người dùng, phân quyền, và cấu hình hệ thống cốt lõi.
- **performance_schema:** Giám sát tài nguyên, đo lường thời gian thực thi lệnh và hiệu năng máy chủ.
- **sys:** Tập hợp các views và hàm giúp người dùng đọc hiểu các số liệu từ performance_schema dễ dàng hơn.