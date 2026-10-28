+++
title = "Cấu hình EC2 Instance"
date = 2024
weight = 1
chapter = false
pre = "<b>5.1. </b>"
+++

#### Khởi chạy một Amazon EC2 Instance

**ℹ️ Thông tin**: **Amazon Elastic Compute Cloud (Amazon EC2)** cung cấp khả năng tính toán có thể thay đổi quy mô trong đám mây AWS. Sử dụng các EC2 instance giúp loại bỏ nhu cầu đầu tư vào phần cứng trả trước, cho phép bạn phát triển và triển khai ứng dụng nhanh hơn.

Trong AWS Management Console, tìm kiếm và chọn **EC2** trên thanh tìm kiếm.

![5.1/1](/images/5-configure-ec2/5.1/1.png)

#### Tạo EC2 Instance của bạn

Trong bảng điều khiển EC2:

- Chọn **Instances** từ ngăn điều hướng bên trái.
- Nhấp vào nút **Launch Instances**.
- Đặt tên cho instance là `my-server`.

![5.1/2](/images/5-configure-ec2/5.1/2.png)


  
**💡 Mẹo**: Sử dụng các quy ước đặt tên mang tính mô tả bao gồm môi trường, dự án và mục đích để việc quản lý tài nguyên dễ dàng hơn khi hạ tầng của bạn phát triển.

![5.1/3](/images/5-configure-ec2/5.1/3.png)

#### Cấu hình Amazon Machine Image (AMI)

- Chọn hệ điều hành **Ubuntu**.
- Chọn AMI **Ubuntu Server 24.04 LTS**.

**ℹ️ Thông tin**: Ubuntu Server 24.04 LTS cung cấp hỗ trợ dài hạn đến năm 2029, đảm bảo tính ổn định và các bản cập nhật bảo mật cho khối lượng công việc sản xuất của bạn.

![5.1/4](/images/5-configure-ec2/5.1/4.png)

#### Chọn Instance Type và Xác thực

1. Instance type **t3.micro** (2 vCPU, 4 GiB memory).
2. Chọn **Create new key pair**.

**🔒 Lưu ý bảo mật**: Key pairs là thiết yếu để truy cập SSH bảo mật vào instance của bạn. Hãy lưu trữ tệp khóa riêng tư (private key) một cách an toàn và không bao giờ chia sẻ nó. Khóa riêng tư không thể khôi phục nếu bị mất.

![5.1/5](/images/5-configure-ec2/5.1/5.png)

3. Phần tạo key pair: 
- Key pair name: `fcaj-lab-key`
- Key pair type: **RSA**
- Private key file format: **.pem**
- Nhấp **Create key pair**.

**ℹ️ Thông tin**: Một hộp thoại tải xuống sẽ xuất hiện, bạn cần lưu tệp này cẩn thận vì chúng ta sẽ sử dụng lại nó.

![5.1/6](/images/5-configure-ec2/5.1/6.png)

#### Cấu hình Mạng và Bảo mật (Network and Security)

Cuộn xuống phần cài đặt mạng:
- Nhấp vào nút **Edit**.
- VPC: **fcaj-lab-vpc**.
- Subnet: Chọn **public subnet**.
- Auto-assign public IP: **Enable**.
- Chọn **Select existing security group**.
- Chọn **fcaj-sg-public**.
- Nhấp **Launch Instance**.

**⚠️ Cảnh báo**: Đặt các EC2 instance trong public subnet sẽ khiến chúng tiếp xúc trực tiếp với internet. Hãy đảm bảo các quy tắc security group của bạn được cấu hình đúng cách để chỉ cho phép các lưu lượng truy cập cần thiết.
![5.1/6](/images/5-configure-ec2/5.1/7.png)

#### Gắn IAM Role để truy cập Amazon ECR

**ℹ️ Thông tin**: Identity and Access Management (IAM) roles cho phép EC2 instance của bạn truy cập an toàn các dịch vụ AWS khác mà không cần nhúng thông tin xác thực vào mã nguồn ứng dụng.

Trong trang chi tiết EC2 instance:

- Chọn EC2 instance **my-server** của bạn.
- Nhấp **Actions**.
- Điều hướng đến **Security**.
- Chọn **Modify IAM role**.

![5.1/7](/images/5-configure-ec2/5.1/8.png)

- Chọn IAM role `CustomRWECRRole`
- Nhấp **Update IAM role**.

**💡 Mẹo**: **CustomRWECRRole** cung cấp quyền đọc và ghi vào Amazon Elastic Container Registry (ECR), cho phép instance của bạn pull và push các container images mà không cần cấu hình thông tin xác thực rõ ràng.

![5.1/10](/images/5-configure-ec2/5.1/9.png)
