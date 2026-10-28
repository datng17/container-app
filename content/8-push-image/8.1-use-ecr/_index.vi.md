+++
title = "Sử dụng ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Tạo ECR Repository cho Frontend Image

1. Tìm kiếm `Elastic Container Registry`. Chọn **Create**

![8.1.1.png](/images/8-push-image/8.1/1.png)

2. Đầu tiên, tạo repository để lưu trữ image cho frontend app. Ở thanh bên trái, chọn **Repository** sau đó chọn **Create repository**

![8.1.2.png](/images/8-push-image/8.1/2.png)

- Repository name: `aws-fcaj-container-app-frontend`.

- Image tag mutability: chọn **Mutable**.

- Encryption configuration: giữ mặc định.
- Nhấn **Create** để tạo

![8.1.2.png](/images/8-push-image/8.1/3.png)
![8.1.3.png](/images/8-push-image/8.1/4.png)

3. Image cho frontend app đã được tạo thành công.

![8.1.4.png](/images/8-push-image/8.1/5.png)


#### Tạo ECR Repository cho Backend Image
Tương tự, tiến hành tạo cho Backend Image với thông tin sau:

- Repository name: `aws-fcaj-container-app-backend`.

- Image tag mutability: chọn **Mutable**.

- Encryption configuration: giữ mặc định.

- Nhấn **Create** để tạo

![8.1.5.png](/images/8-push-image/8.1/6.png)
![8.1.5.png](/images/8-push-image/8.1/7.png)
![8.1.5.png](/images/8-push-image/8.1/8.png)


{{% notice note %}}
Chúng ta cần tạo mỗi repository riêng cho từng ứng dụng để dễ dàng quản lý version của Docker images, đặc biệt phục vụ cho việc triển khai CI/CD sau này.
{{% /notice %}}

#### Cài đặt AWS CLI

1. Trước tiên cần cài đặt **unzip**.

```bash
sudo apt install unzip
```

![8.1.8.png](/images/8-push-image/8.1/9.png)

2. Sau đó sử dụng các lệnh dưới đây để cài đặt AWS CLI.

```bash
sudo curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo unzip awscliv2.zip
sudo ./aws/install
```

![8.1.8.png](/images/8-push-image/8.1/10.png)

3. Sau khi cài đặt, kiểm tra version để xác nhận AWS CLI đã được cài thành công.

```bash
aws --version
```

![8.1.8.png](/images/8-push-image/8.1/11.png)

#### Push Frontend Image lên ECR (Push Frontend Image to ECR)

1. Truy cập lại ECR Console

- Chọn `aws-fcaj-container-app-frontend`
- Nhấn **View push commands**

![8.1.13.png](/images/8-push-image/8.1/12.png)

2. Một hộp thoại sẽ xuất hiện và hiển thị danh sách các lệnh.

![8.1/14.png](/images/8-push-image/8.1/13.png)

3. Quay lại EC2 Instance, cần sử dụng Root User để có thể đăng nhập vào ECR với Docker.

{{% notice note %}}
Khi dùng sudo để đăng nhập ECR với Docker, credential sẽ được lưu trong HOME Dir của user đó. Tuy nhiên khi thực hiện push hoặc pull, hệ thống sẽ kiểm tra credential ở Root thay vì HOME Dir trước đó.
{{% /notice %}}

4. Trong AWS Console phần push commands của **aws-fcaj-container-app-frontend**, chạy lệnh sau để xác thực và đăng nhập vào Amazon ECR từ môi trường Docker cục bộ. Trước khi thực hiện, đảm bảo đã cấu hình [**AWS CLI default profile**](https://000011.awsstudygroup.com/vi/3-installcli/)

![8.1/15.png](/images/8-push-image/8.1/14.png)

5. Liệt kê tất cả Docker images hiện có trên máy

```bash
docker image ls
```

![8.1/15.png](/images/8-push-image/8.1/15.png)

6. Trong AWS console phần push commands của **aws-fcaj-container-app-frontend**:

- Chạy **the first command** để lấy authentication token và xác thực Docker client với registry thông qua AWS CLI

![8.1/16.png](/images/8-push-image/8.1/16.png)

- Có thể bỏ qua **the second command** vì image frontend đã được build

- Chạy lệnh thứ ba để gắn tag cho image.

![8.1/16.png](/images/8-push-image/8.1/17.png)

- Chạy **the fourth command** để push image lên repository AWS vừa tạo

![8.1/16.png](/images/8-push-image/8.1/18.png)

#### Push Backend Image lên ECR (Push Backend Image to ECR)

1. Tương tự, xem push command của `aws-fcaj-container-app-backend`, nhớ copy lệnh login.

![8.1/18.png](/images/8-push-image/8.1/19/png)

2. Copy và chạy lại lệnh login (lệnh đầu tiên) để đảm bảo session còn hiệu lực.

![8.1/19/png](/images/8-push-image/8.1/20.png)

Gắn tag phù hợp cho backend image theo định dạng:

{{% notice note %}}
docker tag <source_image>:<tag> <account_id>.dkr.ecr.<region>.amazonaws.com/<repository_name>:<tag>
{{% /notice %}}

![8.1/20.png](/images/8-push-image/8.1/21.png)

3. Cuối cùng, chạy lệnh push để upload backend image lên ECR.

![8.1/21.png](/images/8-push-image/8.1/22.png)

#### Kiểm tra kết quả (Check the result)

Nếu thành công, vào ECR Console, truy cập lần lượt từng repository để xem kết quả.

![8.1/22.png](/images/8-push-image/8.1/23.png) 
![8.1/23.png](/images/8-push-image/8.1/24.png)