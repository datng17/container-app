+++
title = "Cấu hình VPC"
date = 2024
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

#### Cấu hình VPC

1. Tại giao diện AWS console, thực hiện các bước sau:

- Tìm kiếm và chọn **VPC**

![3.1.1](/images/3-preparation/3.1/1.png)

2. Trong giao diện quản lý **VPC**:

- Chọn **Your VPC**
- Nhấp vào **Create VPC**

![3.1.1](/images/3-preparation/3.1/2.png)

3. Bảng cấu hình VPC xuất hiện:

- Chọn **VPC and more**
- Đặt tên là `fcaj-lab`
- Chọn CIDR block `10.0.0.0/16`

![3.1.1](/images/3-preparation/3.1/3.png)

4. Cấu hình kiến trúc VPC:

    - **Number of Availability Zones:** 2 (để đạt khả năng phục hồi tối đa)
    - **Number of public subnets:** 2 (một subnet cho mỗi AZ)
    - **Number of private subnets:** 2 (một subnet cho mỗi AZ)
    - **NAT gateways:** None (chúng ta sẽ giữ chi phí tối thiểu cho bài lab này)

![3.1.1](/images/3-preparation/3.1/4.png)

5. Trong phần VPC endpoint:

- Chọn **None**
- Nhấp vào **Create VPC**

![3.1.1](/images/3-preparation/3.1/5.png)

6. Sau khi tạo VPC, chúng ta sẽ kiểm tra thông tin của VPC mới tạo (fcaj-lab-vpc)

7. Xem lại tổng quan cấu hình VPC:
![3.1.1](/images/3-preparation/3.1/6.png)

#### Cấu hình Public Subnet
**ℹ️ Thông tin:** Để các EC2 instance trong **public subnets** tự động nhận **public IP addresses**, chúng ta cần bật tính năng **auto-assign public IPv4 addresses**.

1. Trong giao diện quản lý VPC, cuộn xuống ở thanh bên trái:

- Chọn **Subnet**
- Chọn một public subnet: **fcaj-lab-subnet-public1-us-east-1a**
- Nhấp vào **Edit subnet settings**

![3.1.1](/images/3-preparation/3.1/7.png)

3. Bảng cấu hình public subnet xuất hiện:

- Tích chọn **Enable auto-assign public IPv4 address**
- Nhấp vào **Save**

![3.1.1](/images/3-preparation/3.1/8.png)

4. Tương tự, chúng ta sẽ cấu hình cho **fcaj-lab-subnet-public-1b**:

- Chọn **fcaj-lab-subnet-public2-us-east-1b**
- Nhấp vào **Action**
- Chọn **Edit subnet settings**

![3.1.1](/images/3-preparation/3.1/9.png)

5. Tích chọn **Enable auto-assign public IPv4 address**. Nhấp vào **Save**

![3.1.1](/images/3-preparation/3.1/10.png)

Như vậy, chúng ta đã hoàn tất cấu hình VPC và bật public IPv4 cho các public subnet.
