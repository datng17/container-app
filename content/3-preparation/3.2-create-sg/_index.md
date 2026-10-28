+++
title = "Security Group configuration"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

#### Security Group Configuration for EC2

1. In the EC2 management interface, in the left selection menu:

- Select **Security Groups**
- Click on **Create security group**
![3.2.1](/images/3-preparation/3.2/1.png)

2. Configure the Security Group:

- In the **Basic details** section:
  - Security group name: `fcaj-sg-public`
  - Description: `Security group for FCAJ Lab`
  - VPC: **fcaj-lab-vpc**

![3.2.1](/images/3-preparation/3.2/2.png)

3. In the **Inbound rules** section, add the following rules:
  - Type: **SSH**, Source: **Anywhere-IPv4**
  - Type: **HTTP**, Source: **Anywhere-IPv4**
  - Type: **HTTPS**, Source: **Anywhere-IPv4**
  - Type: **Custom TCP**, Port range: **3000**, Source: **Anywhere-IPv4**

![3.2.3](/images/3-preparation/3.2/3.png)

4. For the **Outbound rules**, we will also leave it as default. Click on **Create security group**.

![3.2.4](/images/3-preparation/3.2/4.png)


#### Security Group Configuration for Database Instance

1. Similar to the steps for creating a security group for EC2:

- Select **Security Groups**
- Click on **Create security group**

![3.2.1](/images/3-preparation/3.2/5.png)

2. Configure the Security Group:

- In the **Basic details** section:
  - Security group name: `rds-sg`
  - Description: `Security group for RDS database instance`
  - VPC: **fcaj-lab-vpc**

![3.2.5](/images/3-preparation/3.2/6.png)

3. In the **Inbound rules** section:
  - Select Type: **MYSQL/Aurora**
  - Source: Select **fcaj-sg-public**

![3.2.6](/images/3-preparation/3.2/7.png)

4. For the **Outbound rules**, we will also leave it as default. Click on **Create security group**.
![3.2.8](/images/3-preparation/3.2/8.png)

