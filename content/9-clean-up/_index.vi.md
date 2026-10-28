+++
title = "Dọn dẹp tài nguyên"
date = 2024
weight = 9
chapter = false
pre = "<b>9. </b>"
+++

{{% notice warning %}}
**Lưu ý quan trọng:** Trong bài thực hành này, bạn chỉ cần xóa ECR repository: **aws-fcaj-container-app-frontend** để chuẩn bị cho bài thực hành tiếp theo: [Triển khai ứng dụng trên Amazon Elastic Container Service](https://000016.awsstudygroup.com).
{{% /notice %}}

## Xóa ECR repository

```bash
aws ecr delete-repository --repository-name aws-fcaj-container-app-frontend
```

![9-1-1.png](/images/9-clean-up/1.png)

![9-1-2.png](/images/9-clean-up/2.png)
## Xoa1 DockerHub repository

![9-1-3.png](/images/9-clean-up/3.png)
![9-1-4.png](/images/9-clean-up/4.png)
