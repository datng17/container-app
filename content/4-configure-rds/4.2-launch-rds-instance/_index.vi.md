+++
title = "Khởi tạo RDS Instance"
date = 2024
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

#### Tạo RDS Instance
1. Truy cập vào mục: **Databases**. 
2. Chọn: **Create Database**

![RDS](/images/4-rds/4.2/1.png)

3. Chọn loại cơ sở dữ liệu: **MySQL**
4. Chọn phương thức tạo: **Full configuration**

![RDS](/images/4-rds/4.2/2.png)

5. Chọn mẫu (template): **Dev/Test**
6. Chọn **Multi-AZ DB instance**

{{% notice tip%}}
Phần này có thể được điều chỉnh tùy theo nhu cầu để tối ưu hóa chi phí, nhưng có một số hạn chế nhất định, vì vậy điều quan trọng là phải nghiên cứu kỹ lưỡng.
{{% /notice%}}

![RDS](/images/4-rds/4.2/3.png)

7. Cấu hình chi tiết DB instance:
- Nhập DB instance identifier: **`fcaj-rds-instance`**
- Credentials management: **Self managed** 
- Bỏ tích chọn **Auto generate password**
- Tại mục Master username, nhập `admin`
- Tại mục Master password, nhập: **`letmein12345`**

![RDS](/images/4-rds/4.2/4.png)

**ℹ️ Quan trọng:** Không thể xem lại mật khẩu của người dùng quản trị (master user) sau khi thiết lập. Nếu không ghi lại, người dùng có thể cần phải thay đổi nó. Nếu cần thay đổi mật khẩu master user sau khi DB Instance đã sẵn sàng, có thể sử dụng chức năng chỉnh sửa DB Instance.

8. Cấu hình thông số thực thể:

- Chọn **db.m5.large** cho lớp thực thể 
- Chọn **General Purpose SSD (gp3)** cho loại lưu trữ 
- Đặt **Allocated storage** là **20 GiB**

![RDS](/images/4-rds/4.2/5.png)

9. Cấu hình cài đặt kết nối:

- Chọn **Don’t connect to an EC2 compute resource**
- Tại mục **VPC**, chọn **VPC** đã tạo
- Tại mục **Subnet group**, chọn **subnet group đã tạo trước đó**

![RDS](/images/4-rds/4.2/6.png)

10. Cấu hình cài đặt bảo mật:

- Tại mục Public access, chọn **No**
- Tại mục VPC security group, chọn **Choose existing**
- Tại mục Security Group, chọn **fcaj-sg-public**

![RDS](/images/4-rds/4.2/7.png)

11. Cuộn xuống phần **Additional configuration**. Đặt **initial database name** là `fcaj`. Giữ các cài đặt khác ở giá trị mặc định.
![RDS](/images/4-rds/4.2/8.png)

12. Kiểm tra kỹ lại tất cả các cấu hình và nhấp **Create**
![RDS](/images/4-rds/4.2/9.png)

{{% notice tip%}}
Hiện nay khi tạo RDS Instance, AWS cung cấp thông tin tính toán chi phí ngay lập tức. Điều này giúp việc quản lý chi phí trở nên dễ dàng hơn.
{{% /notice%}}

13. Hoàn tất việc tạo **DB instance**, trạng thái sẽ chuyển sang **Available** sau khoảng 15 phút.

![RDS](/images/4-rds/4.2/10.png)
