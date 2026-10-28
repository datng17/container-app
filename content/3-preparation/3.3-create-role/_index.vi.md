+++
title = "Tạo IAM Roles để truy cập ECR"
date = 2024
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++

#### Cấu hình Policy

1. Tại giao diện AWS Console, tìm kiếm và chọn `IAM`

![3.3.1](/images/3-preparation/3.3/1.png)

2. Trong menu lựa chọn bên phải:

- Chọn **Policies**
- Nhấp vào **Create policy**

![3.3.1](/images/3-preparation/3.3/2.png)

3. Trong **Policy Editor**, tìm kiếm và chọn **Elastic Container Registry**

![3.3.1](/images/3-preparation/3.3/3.png)

4. Một bảng chọn quy tắc xuất hiện. Trong phần **List**:
  - Chọn **DescribeImage**
  - Chọn **ListImages**


5. Trong phần **Read**:
  - Chọn **BatchGetImage**
  - Chọn **DescribeRegistry**
  - Chọn **DescribeRepositories**
  - Chọn **GetAccountSetting**
  - Chọn **GetAuthorizationToken**

![3.3.1](/images/3-preparation/3.3/4.png)

6. Trong phần **Resources**:
  - Chọn **Specific**
  - Chọn **Any in this account**
  - Nhấp **Next**

![3.3.1](/images/3-preparation/3.3/5.png)

7. Trong phần Chi tiết Policy:

- Policy name: `ReadECRRepositoryContent`
- Description: `Allow pull images, describe repositories`
- Nhấp **Create policy**

![3.3.1](/images/3-preparation/3.3/6.png)

8. Tương tự, chúng ta sẽ tạo thêm một policy để ghi vào ECR bằng cách nhấp **Create Policy**:

![3.3.1](/images/3-preparation/3.3/7.png)

9. Một bảng chọn quy tắc xuất hiện:

- Trong phần **Read**:
  - Chọn **BatchCheckLayerAvailability**
  - Chọn **GetAuthorizationToken**

- Trong phần **Write**:
  - Chọn **CompleteLayerUpload**
  - Chọn **InitiateLayerUpload**
  - Chọn **PutImage**
  - Chọn **UploadLayerPart**

![3.3.1](/images/3-preparation/3.3/8.png)

10. Trong phần **Resources**:
  - Chọn **Specific**
  - Chọn **Any in this account**
  - Nhấp **Next**

![3.3.1](/images/3-preparation/3.3/9.png)

11. Bảng chi tiết Policy xuất hiện:

- Policy name: `WriteECRRepositoryContent`
- Description: `Allow push and delete images`
- Nhấp **Next** và chọn **Create policy**
![3.3.1](/images/3-preparation/3.3/10.png)

#### Tạo Role cho ECR

1. Trong giao diện quản lý EC2:

- Chọn **Roles**
- Nhấp vào **Create role**

![3.3.1](/images/3-preparation/3.3/11.png)

2. Trong phần Chi tiết Role:

- Trusted entity type: **AWS service**
- Use case: **EC2**
- Nhấp **Next**
![3.3.1](/images/3-preparation/3.3/12.png)

3. Trong phần **Permissions policies**:

- Chọn hai policy chúng ta vừa tạo: `ReadECRRepositoryContent` và `WriteECRRepositoryContent`
- Sau đó nhấp **Next**

![3.3.1](/images/3-preparation/3.3/13.png)

4. Trong phần Chi tiết Role:

- Role name: `CustomRWECRRole`
- Description: `Custom Read and Write role ECS`
- Nhấp **Create role**

![3.3.1](/images/3-preparation/3.3/14.png)
