+++
title = "Thêm cơ sở dữ liệu để thử nghiệm"
date = 2024
weight = 3
chapter = false
pre = "<b>5.3. </b>"
+++

#### Chuẩn bị

Để đảm bảo ứng dụng hoạt động chính xác, chúng ta cần nạp dữ liệu vào RDS instance.
Chúng ta sẽ sử dụng SQL script trong thư mục **aws-fcaj-container-app/database** để chèn dữ liệu. Để thực hiện việc này, trước tiên hãy di chuyển đến thư mục **aws-fcaj-container-app/database** để lấy đường dẫn của script:

```bash
cd aws-fcaj-container-app/database
echo $PWD/init.sql
```
![5.3/4.png](/images/5-configure-ec2/5.3/1.png)

#### Kết nối tới RDS
1. Bây giờ, chúng ta sẽ sử dụng MySQL client đã cài đặt trước đó để kết nối tới RDS instance. Đầu tiên, truy cập vào RDS Console:
- Chọn RDS instance bạn đã tạo trước đó.
- Sao chép Endpoint.
![5.3/4.png](/images/5-configure-ec2/5.3/2.png)

2. Sử dụng lệnh sau để kết nối. Đừng quên thay thế **"rds-endpoint"** bằng RDS endpoint và **"password"** bằng mật khẩu root RDS: **`letmein12345`**
```bash
mysql -h "rds-endpoint" -u admin -p
```
![5.3/4.png](/images/5-configure-ec2/5.3/3.png)

3. Tiếp theo, chúng ta sẽ sử dụng lệnh `source /project/aws-fcaj-container-app/database/init.sql` để thực thi SQL script
![5.3/4.png](/images/5-configure-ec2/5.3/4.png)

#### Kiểm tra kết quả
1. Kiểm tra cơ sở dữ liệu: `SHOW DATABASES;`
![5.3/4.png](/images/5-configure-ec2/5.3/5.png)

2. Kiểm tra dữ liệu: `USE fcajresbar` sau đó `SELECT * FROM Categories;`
![5.3/4.png](/images/5-configure-ec2/5.3/6.png)

