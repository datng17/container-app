+++
title = "Cài đặt các thư viện cần thiết"
date = 2024
weight = 2
chapter = false
pre = "<b>5.2. </b>"
+++

#### Kết nối tới EC2 Instance qua SSH bằng MobaXterm
1. Nhấp vào **my-server**, sao chép địa chỉ **Public IPv4 address**
![5.2/1.png](/images/5-configure-ec2/5.2/1.png)

2. Tải [MobaXterm](https://mobaxterm.mobatek.net/download-home-edition.html) để kết nối tới instance qua SSH trên cổng 22
![5.2/2.png](/images/5-configure-ec2/5.2/2.png)

3. Đây là giao diện của MobaXterm:
![5.2/2.png](/images/5-configure-ec2/5.2/3.png)

4. Chọn **New Session**
![5.2/2.png](/images/5-configure-ec2/5.2/4.png)

5. Tạo một session mới trong MobaXterm với các cấu hình sau:

- Chọn **SSH**
- Tại Remote host, nhập địa chỉ **Public IPv4 address** lấy từ instance
- Tại Specify username, nhập `ubuntu`
- Xác nhận **port 22**
- Chọn **Advanced SSH settings**
- Chọn **Use private key** và chọn **keypair của instance**.
- Nhấp **OK**
![5.2/2.png](/images/5-configure-ec2/5.2/5.png)

#### Cài đặt Docker

1. Chúng ta cần cài đặt Docker để triển khai ứng dụng sau này. Sử dụng các lệnh sau để cài đặt:

```bash
sudo mkdir -p /tools/docker && cd /tools/docker
sudo nano install_docker.sh
```
2. Nội dung của tệp **install_docker.sh**
```bash
#!/bin/bash

sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://docker.com | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://docker.com $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce
sudo systemctl start docker
sudo systemctl enable docker
sudo curl -L "https://github.com(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo usermod -aG docker ubuntu
newgrp docker
docker --version
docker-compose --version
```
3. Chạy script
```bash
sudo chmod +x install_docker.sh
sudo ./install_docker.sh
```
4. Kết quả hiển thị phiên bản của Docker và Docker Compose
![5.2/2.png](/images/5-configure-ec2/5.2/8.png)

#### Cài đặt MySQL Client
1. Để thêm dữ liệu vào RDS instance, chúng ta cần cài đặt MySQL Client. Sử dụng lệnh sau:
```bash
sudo apt install mysql-client
```

2. Kiểm tra phiên bản MySQL Client: `mysql --version`
![5.2/2.png](/images/5-configure-ec2/5.2/9.png)

3. Clone mã nguồn từ GitHub: 
```bash
sudo mkdir -p /project && cd /project
```
![5.2/2.png](/images/5-configure-ec2/5.2/10.png)

```bash
sudo git clone https://github.com/datng17/aws-fcaj-container-app.git
```
![5.2/2.png](/images/5-configure-ec2/5.2/11.png)
