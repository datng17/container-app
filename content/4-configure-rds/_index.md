+++
title = "Launch RDS Instance"
date = 2024
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Overview of RDS

Amazon RDS is a managed database service on AWS, where we can only access and manage at the RDBMS level, not at the operating system level. It includes Aurora, MySQL, PostgreSQL, MSSQL, Oracle, and MariaDB. Amazon RDS provides the following features:

- Automated backups (including logs and database – up to 35 days).
- Read Replica creation to serve read workloads (reporting).
- Read Replicas can be detached and promoted to a Primary node.
- Operates with automatic failover, Primary/Standby mechanisms, also known as Multi-AZ.
- RDS is commonly used for OLTP applications.
- RDS provides data encryption features both at rest and in transit.
- RDS is also protected by firewall features similar to EC2 (Security Group and NACL).
- Scaling (changing instance size).
- Automatic storage scaling (Storage Auto Scale).
