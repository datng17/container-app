+++
title = "Install Dependencies"
date = 2024
weight = 3
chapter = false
pre = "<b>2.1. </b>"
+++

{{% notice note%}}
In this article, we will practice on a Windows machine.
{{% /notice%}}

#### Install NodeJS
1. Go to [this page](https://nodejs.org/en/download/current) to download Node.js **v25.8.1**
![note](/images/2-deploy-local/2.1/1.png)
2. For better understanding, you should follow the video below to install NodeJS on your personal computer.

{{< youtube 4FAtFwKVhn0 >}}

#### Install MySQL Community
1. Go to [this page](https://dev.mysql.com/downloads/installer/) to download MySQL Community **v8.0.45**
![note](/images/2-deploy-local/2.1/2.png)

2. Similarly, watch this video to install MySQL:

{{< youtube u96rVINbAUI >}}

Some notes when installing MySQL:

- You should install both **MySQL Client** and **MySQL Server** for easier testing. Also, install **MySQL Workbench** and **MySQL Shell**, which is a database management system similar to Microsoft SQL Server Management Studio for Microsoft SQL Server. You may need them in some future projects.
- In MySQL, there are two types of users: Root User and other users, each with different roles. Always remember the password for the Root User: `letmein12345`, and add a new account when installing MySQL Server.
![note](/images/2-deploy-local/2.1/3.png)

#### Results

Once NodeJS is installed, npm will also be included in the package. Check whether NodeJS and npm have been successfully installed using the following two commands:

```bash
node -v
npm -v
```

![note](/images/2-deploy-local/2.1/4.png)

#### Using MySQL Shell

1. Search for `MySQL Shell` in the Windows search bar, then select `MySQL Shell`.

![note](/images/2-deploy-local/2.1/5.png)

2. When opened, you will see the following interface:

![note](/images/2-deploy-local/2.1/6.png)

3. Type `\sql` to switch the Input Mode to MySQL.

![2.1.4](/images/2-deploy-local/2.1/7.png)

4. Then, connect to the MySQL Server by running: `\connect root@localhost`

![2.1.5](/images/2-deploy-local/2.1/8.png)

{{% notice note%}}
If you didn’t create a user during the MySQL installation, you can connect to the MySQL Server using the Root User. In that case, the **connection string** will be `root@localhost`, and don't forget to enter the Root User password you set during installation.
{{% /notice%}}

5. Use the `SHOW DATABASES;` command to check the result again.

![2.1.5](/images/2-deploy-local/2.1/9.png)

**The roles of these four default databases are as follows:**

- **information_schema:** Stores metadata regarding tables, columns, data types, access privileges, etc.
- **mysql:** Contains user information, privileges, and core system configurations.
- **performance_schema:** Monitors resources and measures statement execution times and server performance.
- **sys:** A collection of views and functions that make it easier for users to interpret data from the performance_schema.