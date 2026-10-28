+++
title = "Kiểm tra ứng dụng"
date = 2024
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++

#### Kết quả triển khai

1. Quay lại EC2 Console, sao chép **Public IPv4 address** của EC2 instance mà chúng ta đã sử dụng, sau đó mở trình duyệt và nhập URL như sau:

```
http://public-dns-of-your-ec2:3000
```

![6.2.1.png](/images/6-docker-image/6.2/1.png)

{{% notice note%}}
NginX đang chạy trên port 80 bên trong container. Khi chúng ta gửi request tới URL trên, container sẽ ánh xạ (map) từ port 3000 sang port 80.
{{% /notice%}}

![6.2.2.png](/images/6-docker-image/6.2/2.png)

2. Thử đăng nhập bằng một tài khoản người dùng. Nếu đăng nhập thành công, điều đó có nghĩa là ứng dụng đang hoạt động đúng và sẽ chuyển hướng (redirect) đến giao diện chính.

![6.2.3.png](/images/6-docker-image/6.2/3.png)

![6.2.4.png](/images/6-docker-image/6.2/4.png)

3. Mở thêm một số trang khác.

![6.2.4.png](/images/6-docker-image/6.2/5.png)
![6.2.4.png](/images/6-docker-image/6.2/6.png)
4. Chúng ta đã triển khai ứng dụng thành công bằng Docker Images. Ở phần tiếp theo, chúng ta sẽ sử dụng một cách tiếp cận khác bằng cách triển khai ứng dụng với Docker Compose. Giải pháp này giúp việc triển khai và quản lý container trở nên dễ dàng hơn.