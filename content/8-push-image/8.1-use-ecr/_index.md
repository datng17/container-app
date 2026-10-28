+++
title = "Using ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Create ECR Repository for Backend Image

1. Search for `Elastic Container Registry`. Select **Create**

![8.1.1.png](/images/8-push-image/8.1/1.png)

2. First is to create a repository to store images for the frontend app. In the left panel, choose **Repository** then **Create repository**

![8.1.2.png](/images/8-push-image/8.1/2.png)

- Repository name: `aws-fcaj-container-app-backend`.

- Image tag mutability: select **Mutable**.

- Encryption configuration: leave it as default.
- Click **Create** to create

![8.1.2.png](/images/8-push-image/8.1/3.png)


3. Image for the backend app created successfully.
![8.1.4.png](/images/8-push-image/8.1/5.png)


#### Create ECR Repository for Frontend Image

Similarly, now we will create for Frontend Image. With the following information:

- Repository name: `aws-fcaj-container-app-frontend`.

- Image tag mutability: select **Mutable**.

- Encryption configuration: leave it as default.

- Click **Create** to create

![8.1.5.png](/images/8-push-image/8.1/6.png)
![8.1.5.png](/images/8-push-image/8.1/7.png)
![8.1.5.png](/images/8-push-image/8.1/8.png)



{{% notice note %}}
We need to create each repository for each different application to manage the version of Docker images more easily, especially for future CI/CD implementation.

{{% /notice %}}

#### Install AWS CLI
1. First we need to download **unzip** first.

```bash
sudo apt install unzip
```

![8.1.8.png](/images/8-push-image/8.1/9.png)

2. Then we will use the commands below to install AWS CLI.

```bash
sudo curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo unzip awscliv2.zip
sudo ./aws/install
```
![8.1.8.png](/images/8-push-image/8.1/10.png)

3. After installation, we can check the version to confirm that AWS CLI is installed successfully.
```bash
aws --version
```
![8.1.8.png](/images/8-push-image/8.1/11.png)

#### Push Frontend Image to ECR

1. Re-enter ECR Console

- Select `aws-fcaj-container-app-frontend`
- Press **View push commands**

![8.1.13.png](/images/8-push-image/8.1/12.png)

2. A dialog box will pop up and we can see a series of commands.

![8.1/14.png](/images/8-push-image/8.1/13.png)

3. Back to EC2 Instance, we need to use Root User to be able to log in to ECR with Docker.

{{% notice note %}}
Because when a user uses sudo to log in to ECR with Docker, the credential is saved in the HOME Dir of that user. But when you execute the push or pull command, it will see the credential in Root instead of in HOME Dir which was saved when logging in before.

{{% /notice %}}

4. In AWS Console of push commands for **aws-fcaj-container-app-frontend**, run the following command to authenticate and log in to Amazon ECR from your local Docker environment. Before proceeding, ensure you have configured your [**AWS CLI default profile**](https://000011.awsstudygroup.com/vi/3-installcli/)

![8.1/15.png](/images/8-push-image/8.1/14.png)

5. List all available Docker images on your local machine
```bash
docker image ls
```
![8.1/15.png](/images/8-push-image/8.1/15.png)

6. In the AWS console of push commands for **aws-fcaj-container-app-frontend**:
- Run **the first command** to retrieve an authentication token and authenticate your Docker client with your registry using the AWS CLI
![8.1/16.png](/images/8-push-image/8.1/16.png)

- You can skip **the second command** as your frontend image is already built

- Run the third command to tag your image.

![8.1/16.png](/images/8-push-image/8.1/17.png)

- Run **the fourth command** to push the image to your newly created AWS repository
![8.1/16.png](/images/8-push-image/8.1/18.png)
#### Push Backend Image to ECR

1. Similarly, we will also view the push command of `aws-fcaj-container-app-backend`, remember to copy the login command.

![8.1/18.png](/images/8-push-image/8.1/19.png)

2. Copy and run the login command (the first command) again to ensure your session is active.

![8.1/19/png](/images/8-push-image/8.1/20.png)

![8.1/20.png](/images/8-push-image/8.1/21.png)

3. Finally, execute the push command to upload your backend image to ECR.

![8.1/21.png](/images/8-push-image/8.1/22.png)

#### Check the result

If successful, go to ECR Console, go to each repositories in turn, we can see the result here.
![8.1/22.png](/images/8-push-image/8.1/23.png) 
![8.1/23.png](/images/8-push-image/8.1/24.png)
