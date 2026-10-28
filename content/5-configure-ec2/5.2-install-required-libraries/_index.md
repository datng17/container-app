+++
title = "Install required libraries"
date = 2024
weight = 2
chapter = false
pre = "<b>5.2. </b>"
+++

#### Connecting to your EC2 Instance via SSH using MobaXterm
1. Click to **my-server**, copy **Public IPv4 address**
![5.2/1.png](/images/5-configure-ec2/5.2/1.png)

2. Download [MobaXterm](https://mobaxterm.mobatek.net/download-home-edition.html) to connect to the instance via SSH on port 22
![5.2/2.png](/images/5-configure-ec2/5.2/2.png)

3. This is the interface of MobaXterm:
![5.2/2.png](/images/5-configure-ec2/5.2/3.png)

4. Choose **New Session**
![5.2/2.png](/images/5-configure-ec2/5.2/4.png)

5. Create a new session in MobaXterm with the following configurations:

- Select **SSH**
- For Remote host, enter the **Public IPv4 address** retrieved from the instance
- For Specify username, enter `ubuntu`
- Verify **port 22**
- Select **Advanced SSH settings**
- Select **Use private key** and select **keypair of instance**.
- Click **OK**
![5.2/2.png](/images/5-configure-ec2/5.2/5.png)

#### Install Docker

1. We need to install Docker to deploy applications later. We will use the following commands to install:

```bash
sudo mkdir -p /tools/docker && cd /tools/docker
sudo nano install_docker.sh
```

2. Content of the `install_docker.sh` file:

```bash
#!/bin/bash

sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce
sudo systemctl start docker
sudo systemctl enable docker
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo usermod -aG docker ubuntu
newgrp docker
docker --version
docker-compose --version
```
![5.2/2.png](/images/5-configure-ec2/5.2/7.png)

3. Run the script:
```bash
sudo chmod +x install_docker.sh
sudo ./install_docker.sh
```

4. The results show the versions of Docker and Docker Compose:
![5.2/2.png](/images/5-configure-ec2/5.2/8.png)


#### Install MySQL Client

1. To add data to the RDS instance, we need to install the MySQL Client. Use the following command:

```bash
sudo apt install mysql-client
```

2. Check version MySQL Client: `mysql --version`
![5.2/2.png](/images/5-configure-ec2/5.2/9.png)

### Clone the source code from GitHub

1. Before proceeding to the next steps, we need to clone the project source code.

```bash
sudo mkdir -p /project && cd /project
```
![5.2/2.png](/images/5-configure-ec2/5.2/10.png)

```bash
sudo git clone https://github.com/datng17/aws-fcaj-container-app.git
```
![5.2/2.png](/images/5-configure-ec2/5.2/11.png)