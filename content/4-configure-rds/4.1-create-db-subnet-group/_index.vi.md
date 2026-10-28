+++
title = "Tạo DB Subnet Group"
date = 2024
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

#### Tạo DB Subnet Group trong Amazon RDS

**ℹ️ Thông tin**: DB Subnet Group là một tập hợp các subnet được chỉ định cho cơ sở dữ liệu RDS của bạn trong một VPC. Subnet groups cho phép Amazon RDS cung cấp các địa chỉ IP từ subnet group khi khởi tạo các instance cơ sở dữ liệu.

#### Các bước thực hiện

1. Truy cập Amazon RDS từ AWS Management Console:
   - Tìm kiếm từ khóa: **RDS** 

![RDS](/images/4-rds/4.1/1.png)

   - Chọn mục: **Subnet groups**
   - Nhấp: **Create DB subnet group**

![RDS](/images/4-rds/4.1/2.png)

2. Cấu hình thông tin cơ bản:
   - Nhập tên: **`fcaj-subnet-group`**
   - Nhập mô tả: **`Subnet Group for FCAJ Management`**
   - Chọn VPC đã tạo trước đó **fcaj-lab-vpc**

![RDS](/images/4-rds/4.1/3.png)

3. Cấu hình Subnets:
   - Chọn các **Availability Zones** đã được tạo cùng với **VPC**
   - Chọn 2 **Subnet private**
   - Kiểm tra lại và nhấp **Create**

![RDS](/images/4-rds/4.1/4.png)

**💡 Mẹo**: Sử dụng nhiều Availability Zones giúp tăng tính khả dụng (availability) và khả năng chịu lỗi (fault tolerance) cho cơ sở dữ liệu của bạn.

**🔒 Lưu ý bảo mật**: Luôn đặt các cơ sở dữ liệu RDS trong các private subnet để tăng cường bảo mật và tránh truy cập trực tiếp từ internet.

4. Sau khi tạo thành công, bạn sẽ thấy DB Subnet Group mới trong danh sách

![RDS](/images/4-rds/4.1/5.png)
