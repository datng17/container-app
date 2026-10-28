+++
title = "Test Application"
date = 2024
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++

#### Deployment Results

1. Go back to the EC2 Console, copy the Public IPv4 address of the EC2 instance we've been working on, and then open a browser and enter the URL as follows:

```
http://public-dns-of-your-ec2:3000
```

![6.2.1.png](/images/6-docker-image/6.2/1.png)

{{% notice note%}}
NginX is running on port 80 inside the container. When we make a request to the above URL, the container will map from port 3000 to 80.
{{% /notice%}}

![6.2.2.png](/images/6-docker-image/6.2/2.png)

2. Try logging in with a user account. If the login is successful, it means our application is running properly and will redirect us to the main interface.

![6.2.3.png](/images/6-docker-image/6.2/3.png)

![6.2.4.png](/images/6-docker-image/6.2/4.png)

3. Open some additional pages.
![6.2.4.png](/images/6-docker-image/6.2/5.png)
![6.2.4.png](/images/6-docker-image/6.2/6.png)

4. We've successfully deployed the application using Docker Images. In the next section, we'll use a different approach by deploying the application with Docker Compose. This solution will make it easier to deploy and manage containers.