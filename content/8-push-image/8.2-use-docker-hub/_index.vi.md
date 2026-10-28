+++
title = "Sử dụng Docker Hub"
date = 2024
weight = 2
chapter = false
pre = "<b>8.2. </b>"
+++

#### Tạo repository trên Docker Hub

1. Truy cập [**Docker Hub**](https://hub.docker.com/repositories), đã được chuẩn bị trước, và tạo repository tại đây.  
2. Kéo xuống và nhấn **Create repository**

![8.2.1.png](/images/8-push-image/8.2/1.png)

- Chọn **Namespace** là tài khoản của bạn.  
- Nhập tên repository: `aws-fcaj-container-app-frontend`  
- Nhập mô tả: `Frontend Image of FCAJ Resbar`  
- Chọn Visibility: **Public**  
- Kiểm tra và chọn **Create**

![8.2.2.png](/images/8-push-image/8.2/2.png)

3. Tạo **repository** trên **Docker Hub** thành công.

![8.2/3.png](/images/8-push-image/8.2/3.png)

4. Tương tự, tạo repository cho backend image.

- Chọn **Namespace** là tài khoản của bạn.  
- Nhập tên repository: ` aws-fcaj-container-app-backend`.  
- Nhập mô tả: `Backend Image of FCAJ Resbar`.  
- Chọn Public.  
- Kiểm tra và chọn **Create**.

![8.2/4.png](/images/8-push-image/8.2/4.png)

5. Tạo **repository** trên **Docker Hub** thành công.

![8.2.5.png](/images/8-push-image/8.2/5.png)

#### Push frontend và backend image lên Docker Hub

1. Chạy lệnh `docker login` để xác thực. Nếu đang đăng nhập bằng tài khoản khác, hãy đăng xuất trước, sau đó đăng nhập lại bằng tài khoản tương ứng với repository của bạn.

![8.2.6.png](/images/8-push-image/8.2/6.png)

2. Liệt kê tất cả Docker images hiện có trên máy

```bash
docker image ls
```

![8.2.6.png](/images/8-push-image/8.2/7.png)

3. Gắn tag cho **Frontend Image** và **Backend Image**

```bash
docker tag aws-fcaj-container-app-frontend <username>/aws-fcaj-container-app-frontend
docker tag aws-fcaj-container-app-backend <username>/ aws-fcaj-container-app-backend
```

![8.2.6.png](/images/8-push-image/8.2/8.png)

4. Push các image lên Docker Hub

```bash
docker push <username>/aws-fcaj-container-app-frontend
docker push <username>/ aws-fcaj-container-app-backend
```

![8.2.6.png](/images/8-push-image/8.2/9.png)

{{% notice note %}}
Nếu không chỉ định tag trong lệnh `docker tag`, hệ thống sẽ tự động gán tag `latest` cho image.
{{% /notice %}}

#### Kết quả

Sau khi push, chúng ta có thể thấy các image đã được đưa lên các repository tương ứng.

![8.2.10.png](/images/8-push-image/8.2/10.png)

![8.2.11.png](/images/8-push-image/8.2/11.png)
