+++
title = "Clean up resources"
date = 2024
weight = 9
chapter = false
pre = "<b>9. </b>"
+++

{{% notice warning %}}
**Important Notice:** In this lab, you only need to delete ECR repository: **aws-fcaj-container-app-frontend** to prepare for the next lab: [Deploy applications on Amazon Elastic Container Service](https://000016.awsstudygroup.com).
{{% /notice %}}

## Delete ECR repository

```bash
aws ecr delete-repository --repository-name aws-fcaj-container-app-frontend
```

![9-1-1.png](/images/9-clean-up/1.png)

![9-1-2.png](/images/9-clean-up/2.png)

## Delete DockerHub repository

![9-1-3.png](/images/9-clean-up/3.png)
![9-1-3.png](/images/9-clean-up/4.png)