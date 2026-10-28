+++
title = "Cấu hình Security Group"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

#### Cấu hình Security Group cho EC2

1. Trong giao diện quản lý EC2, tại menu lựa chọn bên trái:

- Chọn **Security Groups**
- Nhấp vào **Create security group**

![3.2.1](/images/3-preparation/3.2/1.png)
2. Cấu hình Security Group:

- Trong phần **Basic details**:
  - Security group name: `fcaj-sg-public`
  - Description: `Security group for FCAJ Lab`
  - VPC: **fcaj-lab-vpc**
![3.2.1](/images/3-preparation/3.2/2.png)

3. Trong phần **Inbound rules**, thêm các quy tắc (rules) sau:
  - Type: **SSH**, Source: **Anywhere-IPv4**
  - Type: **HTTP**, Source: **Anywhere-IPv4**
  - Type: **HTTPS**, Source: **Anywhere-IPv4**
  - Type: **Custom TCP**, Port range: **3000**, Source: **Anywhere-IPv4**

![3.2.1](/images/3-preparation/3.2/3.png)

4. Đối với **Outbound rules**, chúng ta sẽ để mặc định. Nhấp vào **Create security group**.

![3.2.1](/images/3-preparation/3.2/4.png)


#### Cấu hình Security Group cho Database Instance

1. Tương tự như các bước tạo security group cho EC2:

- Chọn **Security Groups**
- Nhấp vào **Create security group**

![3.2.1](/images/3-preparation/3.2/5.png)

2. Cấu hình Security Group:

- Trong phần **Basic details**:
  - Security group name: `rds-sg`
  - Description: `Security group for RDS database instance`
  - VPC: **fcaj-lab-vpc**

![3.2.1](/images/3-preparation/3.2/6.png)

3. Trong phần **Inbound rules**:
  - Chọn Type: **MYSQL/Aurora**
  - Source: Chọn **fcaj-sg-public**

![3.2.1](/images/3-preparation/3.2/7.png)

4. Đối với **Outbound rules**, chúng ta cũng sẽ để mặc định. Nhấp vào **Create security group**.
![3.2.1](/images/3-preparation/3.2/8.png)
