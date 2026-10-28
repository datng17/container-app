+++
title = "Launch RDS Instance"
date = 2024
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++

#### Create RDS Instance
1. Go to the section: **Databases**. 
2. Select: **Create Database**

![RDS](/images/4-rds/4.2/1.png)

3. Choose database type: **MySQL**
4. Select create method: **Full configuration**

![RDS](/images/4-rds/4.2/2.png)

5. Select the template: **Dev/Test**
6. Choose **Multi-AZ DB instance**

{{% notice tip%}}
This section can be adjusted according to your needs to optimize costs, but there are some limitations, so it's important to research carefully.
{{% /notice%}}

![RDS](/images/4-rds/4.2/3.png)

7. Configure DB instance details:
- Enter the DB instance identifier: **`fcaj-rds-instance`**
- Credentials management: **Self managed**
- Uncheck **Auto generate password**
- For Master username, enter `admin`
- For Master password, enter: **`letmein12345`**

![RDS](/images/4-rds/4.2/4.png)

**ℹ️ Important:** You cannot review the master user password. If you don’t record it, you may need to change it. If you need to change the master user password after the DB Instance is available, you can modify the DB Instance to do this. For more information on modifying a DB Instance, see Modifying an Amazon RDS DB Instance.

8. Configure instance specifications:

- Select **db.m5.large** for the instance class
- Choose **General Purpose SSD (gp3)** for storage type
- Set **Allocated storage** to **20 GiB**

![RDS](/images/4-rds/4.2/5.png)

9/ Configure connectivity settings:

- Select **Don’t connect to an EC2 compute resource**
- For **VPC**, select your created **VPC**
- For **Subnet group**, choose the **subnet group you created earlier**

![RDS](/images/4-rds/4.2/6.png)

10. Configure security settings:

- For Public access, select **No**
- For VPC security group, select **Choose existing**
- For Security Group, select **fcaj-sg-public**

![RDS](/images/4-rds/4.2/7.png)

11. Scroll down to **Additional configuration** section. Set the **initial database name** to `fcaj`. Leave other settings at their default values
![RDS](/images/4-rds/4.2/8.png)

12. Review all configurations carefully and click **Create**
![RDS](/images/4-rds/4.2/9.png)

{{% notice tip%}}
Currently when creating RDS Instance, AWS provides cost calculation information immediately when creating the instance. This helps you easily manage costs.
{{% /notice%}}

13. Complete the creation of the **DB instance**, it will take about 15 minutes to become **Available**

![RDS](/images/4-rds/4.2/10.png)

