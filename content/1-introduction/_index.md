+++
title = "Introduction"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Overview

![1.1](/images/1-introduction/1.2.png)

In this workshop, we will practice deploying applications to Docker Containers, from building to managing the entire operation process. You will explore how to leverage the power of popular tools and services in a containerized environment such as Docker Hub, Nginx, Amazon ECR, Amazon RDS, and Amazon EC2.

The services used in this workshop include:

- **Docker Hub**: This is the most popular Docker image repository service, allowing you to easily store and share application images, enabling quick deployment anywhere.

- **Nginx**: One of the most powerful web servers, often used as a reverse proxy and load balancer, optimizing application distribution and ensuring high scalability.

- **Amazon Elastic Container Registry (ECR)**: ECR is a secure Docker image repository service, tightly integrated with AWS services, enabling you to manage, store, and deploy Docker images directly from the cloud environment.

- **Amazon Relational Database Service (RDS)**: RDS is a fully managed database service that automates maintenance tasks and optimizes database performance. In this workshop, you will learn how to integrate your Docker application with RDS, ensuring high performance and strong security.

- **Amazon EC2**: EC2 provides flexible and powerful cloud servers for deploying, running containers, and managing your containerized applications on AWS infrastructure.

####  Workflow

1. **User Request (Client-Side)**:

- The **user** initiates a request from their browser or device, such as accessing a website or application.
- This request is routed through the **Internet**, where it begins the journey toward your application infrastructure.

2. **Internet Gateway (AWS Infrastructure)**:

- The request first passes through the **Internet Gateway** in your cloud infrastructure, typically hosted on AWS. The Internet Gateway serves as a link between the public internet and your Virtual Private Cloud (VPC).
- It forwards incoming traffic to the Nginx server within your infrastructure.

3. **Nginx (Reverse Proxy & Load Balancer)**:

- **Nginx** receives the request and acts as a **reverse proxy** to direct traffic to the appropriate application containers.
- Nginx is responsible for routing the request either to the **Frontend container** (for handling the user interface and client-side logic) or the **Backend container** (which processes business logic and interacts with the database).

4. **Frontend and Backend Containers**:

- The **Frontend container** (often built with frameworks like React, Vue.js, etc.) handles the user interface and presentation layer of the application. It sends requests to the backend for any server-side logic or data retrieval.
- The **Backend container** (often built with Node.js, Python, etc.) processes the request, applies business logic, and makes a call to the database for data retrieval or storage.

5. **Amazon RDS (Database Layer)**:

- The **backend container** communicates with **Amazon RDS** (Relational Database Service), where the application’s data is stored.
- The backend retrieves the necessary data from RDS, such as user information, quiz results, or any other database interactions required by the application.

6. **Responding to the User**:

- Once the backend retrieves the data from RDS and processes the request, it sends the response back to the **frontend container** via Nginx.
- The frontend renders the response and sends it back to the **user**, completing the cycle.

7. **Pushing Docker Images to Docker Hub and Amazon ECR**:

- Separately from the request-response cycle, when you make changes to your application or infrastructure, the updated **Docker images** (for both frontend and backend) are **pushed** to **Docker Hub** or **Amazon ECR** (Elastic Container Registry).
- These repositories securely store the images, making them available for future deployments. This allows you to easily redeploy your updated containers on EC2 instances or other environments.
