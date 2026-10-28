+++
title = "Test Application"
date = 2024
weight = 5
chapter = false
pre = "<b>2.3. </b>"
+++

#### Check Deployment Results
**ℹ️ Information**: Before you access http://localhost:5173/, make sure that the `npm run dev` command is running in both the **frontend and backend folders**

1. We need to go to the URL: `http://localhost:5173`. At that point, you will see the following interface:

![2.3.1](/images/2-deploy-local/2.3/1.png)

#### User Authentication

**🔒 Security Note**: Use one of the following accounts to log in to the application:

- User: email `user@example.com`; password `123456`.
- Admin: email `admin@example.com`; password `123456`.

**⚠️ Warning**: In a real production environment, you should use AWS IAM Identity Center or Amazon Cognito for more secure authentication.

#### Check Interface

1. After successfully logging in with the **admin account**, you will see the following content on the website:
![2.3.1](/images/2-deploy-local/2.3/2.png)

**💡 Pro Tip**: Take a look at some other pages to check the navigation and display features, such as the **Users and Clients pages**:

![2.3.1](/images/2-deploy-local/2.3/3.png)

![2.3.1](/images/2-deploy-local/2.3/4.png)