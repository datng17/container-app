+++
title = "Triển khai Application"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

Ở phần **2 Deploy on Local** trước đó thì chúng ta đã triển khai thủ công lần lượt là

- Database Server
- Web Server
- End User Application

Có rất nhiều mặt hạn chế như mình đã nói trước đó, nên giờ chúng ta sẽ triển khai hạ tầng này ở trên Cloud với Docker, nên là việc tải về và cài đặt chúng ta sẽ không còn lo nữa. Nếu như bạn nắm được các khái niệm cơ bản của Docker (đặt biệt là mạng) thì phần này sẽ không quá khó.

Và ở bước **4 Configure RDS** trước đó thì chúng ta đã cấu hình Database Server với Amazon RDS, nên về mặt kỹ thuật, bảo trì và đảm bảo về truy cập cũng như an toàn dữ liệu thì mình sẽ không cần phải lo quá nhiều nữa. Nên là trong phần triển khai trên Cloud này thì mình chỉ quan tâm tới triển khai các ứng dụng còn lại với Docker Image.

Ở phần sau thì chúng ta sẽ triển khai với Docker Compose, để cho bạn có thể thấy được sự khác biệt khi deploy ở Local, với Docker Image trên Cloud và với Docker Compose trên Cloud.

{{% notice note %}}
Ở trong phần triển khai 2 Deploy on Local thì bạn có thể xem như là chúng ta đang triển khai ở trong môi trường phát triển, nhưng giờ sẽ triển khai ở môi trường sản phẩm hoặc là môi trường kiểm thử.
{{% /notice %}}

#### Triển khai Web Server

1. Vào trong thư mục mã nguồn mà chúng ta đã clone từ trước đó **aws-fcaj-container-app**, trong thư mục **backend**, chúng ta sẽ sửa lại nội dung của **.env**, cụ thể là thay đổi biến **DB_HOST**: `sudo nano .env`

![6.1.1.png](/images/6-docker-image/6.1/1.png)

![6.1.2.png](/images/6-docker-image/6.1/2.png)

2. Sử dụng `cd backend` để di chuyển vào trong thư mục **backend**. Giờ thì web server của chúng ta cũng đã sẵn sàng để chạy, tiếp theo là chạy lệnh ở bên dưới để build docker image của backend

```bash
docker build -t aws-fcaj-container-app-backend .
```

![6.1.1.png](/images/6-docker-image/6.1/3.png)

3. Trước khi bắt đầu chạy Container cho web server, thì mình sẽ cần phải tạo một **network** cho các container trong môi trường giao tiếp với nhau

```bash
sudo docker network create my-network
```

4. Sau đó là tiến hành chạy Docker Container với Docker Image vừa mới tạo

```bash
sudo docker run -d -p 5000:5000 --network my-network --name backend aws-fcaj-container-app-backend
```

![6.1.1.png](/images/6-docker-image/6.1/4.png)


#### Triển khai Application

1. Giờ chúng ta sẽ phải mở một SSH Session mới để thực hiện tương tự như các bước ở trên, nhưng sẽ là triển khai Application

- cd vào trong thư mục frontend

```bash
cd /projects/aws-fcaj-container-app/frontend
```

2. Chạy lệnh như bên dưới

```bash
docker build -t aws-fcaj-container-app-frontend .
```

![6.1.1.png](/images/6-docker-image/6.1/5.png)

3. Sau đó là tiến hành chạy Docker Container với Docker Image vừa mới tạo

```bash
sudo docker run -d -p 3000:80 --network my-network --name frontend aws-fcaj-container-app-frontend
```

![6.1.1.png](/images/6-docker-image/6.1/6.png)
