+++
title = "Deploying the Application"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Deployment with Docker Compose

1. Create a new SSH session, then navigate to the **docker-compose-env** directory at the root of the project and use `sudo nano backend.app.env` to update the **DB_HOST variable** to your **RDS Endpoint**.

```bash
cd docker-compose-env
sudo nano backend.app.env
```

![7.1.3.png](/images/7-docker-compose/7.1/1.png)

![7.1.4.png](/images/7-docker-compose/7.1/2.png)

2. Return to the **aws-fcaj-container-app** directory, then remove the `frontend` and `backend` containers running from the previous section to free up resources and avoid port conflicts:

```bash
sudo docker rm -f frontend backend
```

![7.1.3.png](/images/7-docker-compose/7.1/3.png)

3. In the **aws-fcaj-container-app** directory, we can simply run:

```bash
cd /project/aws-fcaj-container-app
sudo docker compose -f docker-compose.app.yml up
```

4. This will start the two containers just like we did in the previous section.

![7.1.5.png](/images/7-docker-compose/7.1/4.png)
![7.1.6.png](/images/7-docker-compose/7.1/5.png)


