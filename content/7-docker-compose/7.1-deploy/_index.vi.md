+++
title = "Triển khai ứng dụng"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Triển khai với Docker Compose 

1. Tạo một phiên SSH mới, sau đó truy cập vào thư mục **docker-compose-env** tại thư mục gốc của project và sử dụng `sudo nano backend.app.env` để cập nhật biến **DB_HOST** thành **RDS Endpoint** của bạn.

```bash
cd docker-compose-env
sudo nano backend.app.env
```

![7.1.3.png](/images/7-docker-compose/7.1/1.png)

![7.1.4.png](/images/7-docker-compose/7.1/2.png)

2. Quay lại thư mục **aws-fcaj-container-app**, xóa các container `frontend` và `backend` đã chạy ở phần trước để giải phóng tài nguyên và tránh xung đột cổng:

```bash
sudo docker rm -f frontend backend
```

![7.1.3.png](/images/7-docker-compose/7.1/3.png)

3. Tại thư mục **aws-fcaj-container-app**, chỉ cần chạy:

```bash
cd /project/aws-fcaj-container-app
sudo docker compose -f docker-compose.app.yml up
```

4. Lệnh này sẽ khởi động hai container giống như chúng ta đã thực hiện ở phần trước. Ứng dụng của chúng ta đã chạy thành công

![7.1.5.png](/images/7-docker-compose/7.1/4.png)
![7.1.6.png](/images/7-docker-compose/7.1/5.png)