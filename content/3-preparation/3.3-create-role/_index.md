+++
title = "Create IAM Roles for ECR Access"
date = 2024
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++

#### Policy Configuration

1. In the AWS Console interface, search for and select `IAM`

![3.3.1](/images/3-preparation/3.3/1.png)

2. In the right selection menu:

- Select **Policies**
- Click on **Create policy**

![3.3.2](/images/3-preparation/3.3/2.png)

3. In the **Policy Editor**, search for and select **Elastic Container Registry**

![3.3.3](/images/3-preparation/3.3/3.png)

4. A rule selection panel appears. In the **List** section:
  - Select **DescribeImage**
  - Select **ListImages**


5. In the **Read** section:
  - Select **BatchGetImage**
  - Select **DescribeRegistry**
  - Select **DescribeRepositories**
  - Select **GetAccountSetting**
  - Select **GetAuthorizationToken**

![3.3.4](/images/3-preparation/3.3/4.png)

6. In the **Resources** section:
  - Select **Specific**
  - Select **Any in this account**
  - Click **Next**

![3.3.5](/images/3-preparation/3.3/5.png)

7. In the Policy details section:

- Policy name: `ReadECRRepositoryContent`
- Description: `Allow pull images, describe repositories`
- Click **Create policy**

![3.3.19](/images/3-preparation/3.3/6.png)

8. Similarly, we will create an additional policy for writing to ECR by clicking **Create Policy**:

![3.3.2](/images/3-preparation/3.3/7.png)

9. A rule selection panel appears:

- In the **Read** section:
  - Select **BatchCheckLayerAvailability**
  - Select **GetAuthorizationToken**

- In the **Write** section:
  - Select **CompleteLayerUpload**
  - Select **InitiateLayerUpload**
  - Select **PutImage**
  - Select **UploadLayerPart**

![3.3.6](/images/3-preparation/3.3/8.png)

10. In the **Resources** section:
  - Select **Specific**
  - Select **Any in this account**
  - Click **Next**
![3.3.6](/images/3-preparation/3.3/9.png)

11. The Policy details panel appears:

- Policy name: `WriteECRRepositoryContent`
- Description: `Allow push and delete images`
- Click **Next** and select **Create policy**
![3.3.8](/images/3-preparation/3.3/10.png)

#### Create Role for ECR

1. In the EC2 management interface:

- Select **Roles**
- Click on **Create role**

![3.3.10](/images/3-preparation/3.3/11.png)

2. In the Role details section:

- Trusted entity type: **AWS service**
- Use case: **EC2**
- Click **Next**
![3.3.11](/images/3-preparation/3.3/12.png)

3. In the **Permissions policies** section:

- Select the two policies we just created: `ReadECRRepositoryContent` and `WriteECRRepositoryContent`
- Then we will click **Next**

![3.3.13](/images/3-preparation/3.3/13.png)

4. In the Role details section:

- Role name: `CustomRWECRRole`
- Description: `Custom Read and Write role ECS`
- Click **Create role**

![3.3.17](/images/3-preparation/3.3/14.png)
