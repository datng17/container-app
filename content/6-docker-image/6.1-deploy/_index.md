+++
title = "Deploy Application"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

In the previous section, **2 Deploy on Local**, we manually deployed the following:

- Database Server
- Web Server
- End User Application

As mentioned before, there were several limitations in this approach. Now, we'll deploy the infrastructure on the cloud using Docker, eliminating the need to download and install everything manually. If you're familiar with Docker basics (especially networking), this part will not be too challenging.

In the earlier 4 Configure RDS step, we already configured the Database Server using Amazon RDS, so we no longer need to worry much about maintenance, access security, or data safety. Now, in this cloud deployment, we'll focus on deploying the remaining applications using Docker Images.

Next, we'll deploy using Docker Compose so you can see the difference between deploying on Local, deploying with Docker Images on the Cloud, and deploying with Docker Compose on the Cloud.

{{% notice note %}}
In the 2 Deploy on Local section, you can consider this as deploying in a development environment, but now we'll deploy in a production or testing environment.
{{% /notice %}}

#### Deploy the Web Server

1. Go to the source code directory we cloned earlier, **aws-fcaj-container-app**. Inside the **backend** folder, modify the contents of the **.env** file, specifically changing the **DB_HOST variable**: `sudo nano .env`

![6.1.1.png](/images/6-docker-image/6.1/1.png)

![6.1.2.png](/images/6-docker-image/6.1/2.png)

2. Use `cd backend` to navigate to the **backend** folder. Now the web server is ready to run. 

```bash
docker build -t aws-fcaj-container-app-backend .
```

![6.1.3.png](/images/6-docker-image/6.1/3.png)

3. Before starting the web server container, we need to create a **network** for the containers to communicate with each other:

```bash
sudo docker network create my-network
```

4. Then, run the Docker container using the newly built Docker Image:

```bash
sudo docker run -p 5000:5000 --network my-network --name backend aws-fcaj-container-app-backend

```

![6.1.4.png](/images/6-docker-image/6.1/4.png)

#### Deploy the Application

1. Now, open a **new SSH session** to follow the same steps, but this time, we'll deploy the Application.
- Use `cd frontend` to navigate to the **frontend** folder
- Run the command below:
```bash
docker build -t aws-fcaj-container-app-frontend .
```
![6.1.5.png](/images/6-docker-image/6.1/5.png)

2. Then, run the Docker container using the newly created Docker Image:

```bash
sudo docker run -p 3000:80 --network my-network --name frontend aws-fcaj-container-app-frontend
```

![6.1.7.png](/images/6-docker-image/6.1/6.png)
