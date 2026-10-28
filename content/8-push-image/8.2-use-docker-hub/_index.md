+++
title = "Use Docker Hub"
date = 2024
weight = 2
chapter = false
pre = "<b>8.2. </b>"
+++

#### Create a repository on Docker Hub

1. Go to [**Docker Hub**](https://hub.docker.com/repositories), which has been prepared, and create a repository there.
2. Scroll down and click **Create repository**

![8.2.1.png](/images/8-push-image/8.2/1.png)

- Choose the **Namespace** as your account.
- Enter the repository name: `aws-fcaj-container-app-frontend`
- Enter the description: `Frontend Image of FCAJ Resbar`
- Select Visibility: **Public**
- Review and select **Create**

![8.2.2.png](/images/8-push-image/8.2/2.png)

- Successfully created a **repository** on **Docker Hub**.

![8.2/3.png](/images/8-push-image/8.2/3.png)

3. Similarly, create a repository for the backend image.

- Choose the **Namespace** as your account.
- Enter the repository name: `aws-fcaj-container-app-backend`.
- Enter the description: `Backend Image of FCAJ Resbar`.
- Select public.
- Review and select **Create**.

![8.2/4.png](/images/8-push-image/8.2/4.png)

4. Successfully created a **repository** on **Docker Hub**.

![8.2.5.png](/images/8-push-image/8.2/5.png)

#### Push frontend and backend image to Docker Hub

1. Run the `docker login` command to authenticate. If you are already logged in with a different account, log out first, then log in using the credentials associated with your repositories
![8.2.6.png](/images/8-push-image/8.2/6.png)

2. List all available Docker images on your local machine
```bash
docker image ls
```
![8.2.6.png](/images/8-push-image/8.2/7.png)

3. Tag the **Frontend Image** and **Backend Image**
```bash
docker tag aws-fcaj-container-app-frontend <username>/aws-fcaj-container-app-frontend
docker tag aws-fcaj-container-app-backend <username>/aws-fcaj-container-app-backend
```
![8.2.6.png](/images/8-push-image/8.2/8.png)

4. Push the images to Docker Hub
```bash
docker push <username>/aws-fcaj-container-app-frontend
docker push <username>/aws-fcaj-container-app-backend
```
![8.2.6.png](/images/8-push-image/8.2/9.png)

{{% notice note %}}
If we don't specify a tag in the `docker tag` command, it will automatically add the `latest` tag to the image.
{{% /notice %}}

#### Results

After pushing, we can see that the images have been pushed to their respective repositories.

![8.2.10.png](/images/8-push-image/8.2/10.png)

![8.2.11.png](/images/8-push-image/8.2/11.png)
