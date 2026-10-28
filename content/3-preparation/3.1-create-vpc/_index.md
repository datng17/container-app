+++
title = "VPC configuration"
date = 2024
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

#### VPC Configuration

1. In the AWS console interface, perform the following:

- Search for and select **VPC**

![3.1.1](/images/3-preparation/3.1/1.png)

2. In the **VPC** management interface:

- Select **Your VPC**
- Click on **Create VPC**

![3.1.2](/images/3-preparation/3.1/2.png)

3. The VPC configuration panel appears:

- Choose **VPC and more**
- Name it `fcaj-lab`
- Select CIDR block `10.0.0.0/16`

![3.1.3](/images/3-preparation/3.1/3.png)

4. Configure the VPC architecture:

    - **Number of Availability Zones:** 2 (for maximum resilience)
    - **Number of public subnets:** 2 (one per AZ)
    - **Number of private subnets:** 2 (one per AZ)
    - **NAT gateways:** None (we’ll keep costs minimal for this lab)

![3.1.4](/images/3-preparation/3.1/4.png)

5. In the VPC endpoint section:

- Select **None**
- Click on **Create VPC**

![3.1.5](/images/3-preparation/3.1/5.png)

6. After creating the VPC, we will check the information of the newly created VPC (fcaj-lab-vpc)

7. Review the overview of the VPC configuration:
![3.1.6](/images/3-preparation/3.1/6.png)

#### Public Subnet Configuration
ℹ️ Information: For EC2 instances in **public subnets** to receive **public IP addresses** automatically, we need to enable **auto-assign public IPv4 addresses**.

1. In the VPC management interface, scroll down in the left sidebar:

- Select **Subnet**
- Select a public subnet: **fcaj-lab-subnet-public1-us-east-1a**
- Click **Edit subnet settings**

![3.1.7](/images/3-preparation/3.1/7.png)

3. The public subnet configuration panel appears:

- Check **Enable auto-assign public IPv4 address**
- Click **Save**

![3.1.10](/images/3-preparation/3.1/8.png)

4. Similarly, we will configure **fcaj-lab-subnet-public-1b**:

- Select **fcaj-lab-subnet-public2-us-east-1b**
- Click on **Action**
- Choose **Edit subnet settings**

![3.1.11](/images/3-preparation/3.1/9.png)

5. Check **Enable auto-assign public IPv4 address**. Click **Save**

![3.1.12](/images/3-preparation/3.1/10.png)

Thus, we have configured the VPC and enabled public IPv4 for the public subnets.
