+++
title = "Add Database for testing"
date = 2024
weight = 3
chapter = false
pre = "<b>5.3. </b>"
+++

#### Preparation

To ensure the application works, we need to load data into the RDS instance.
We will use the SQL script in `aws-fcaj-container-app/database` to insert the data. To do this, first navigate to the `aws-fcaj-container-app/database` directory to get the script path:

```bash
cd aws-fcaj-container-app/database
echo $PWD/init.sql
```

![5.3/1.png](/images/5-configure-ec2/5.3/1.png)

Copy the path as we will use it later.

#### Connect to RDS

1. Now, we'll use the MySQL client installed earlier to connect to the RDS instance. First, go to the RDS Console:

- Select the RDS instance you created earlier.
- Copy the endpoint.

![5.3/2.png](/images/5-configure-ec2/5.3/2.png)

2. Use the following command to connect. Don't forget to replace **"rds-endpoint"** with your RDS endpoint and **"password"** with your RDS master password: **`letmein12345`**

```bash
mysql -h "rds-endpoint" -u admin -p
```

![5.3/3.png](/images/5-configure-ec2/5.3/3.png)

3. Next, we will use the `source /project/aws-fcaj-container-app/database/init.sql` command to run the SQL script.

![5.3/4.png](/images/5-configure-ec2/5.3/4.png)

#### Verify Results

1. Check the database: `SHOW DATABASES;`

![5.3/5.png](/images/5-configure-ec2/5.3/5.png)

2. Check the data: `USE fcajresbar` then `SELECT * FROM Categories;`

![5.3/6.png](/images/5-configure-ec2/5.3/6.png)
