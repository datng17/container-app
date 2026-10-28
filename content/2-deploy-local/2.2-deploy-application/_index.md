+++
title = "Deploy Application"
date = 2024
weight = 4
chapter = false
pre = "<b>2.2. </b>"
+++

{{% notice note%}}
To complete this part, you must have Git installed beforehand.
{{% /notice%}}

#### Download Source Code
1. Create a folder with any name. I'll call it `workspace`
2. Right-click and select **Open in Terminal**.

![2.2.1](/images/2-deploy-local/2.2/1.png)

3. Clone the application's source code from GitHub to your machine.

```bash
git clone https://github.com/datng17/fcaj-resbar.git
```

4. And here is the result:

![2.2.1](/images/2-deploy-local/2.2/2.png)

#### Add Data

1. To add data:

- Go to the **database** folder inside the source code folder you downloaded.
- Copy the path from the browse bar in Windows.

![2.2.1](/images/2-deploy-local/2.2/3.png)

2. Run the initialization script using the source command in MySQL Shell. You will need to provide the full absolute path to the **init.sql** file

![2.2.1](/images/2-deploy-local/2.2/4.png)


3. Run some queries to verify:

```sql
SELECT * FROM Clients;
```

![2.2.1](/images/2-deploy-local/2.2/5.png)

#### Deploy Web Server
1. Then open the **Terminal** in this **backend folder**. Proceed to **install the NPM packages** to run the server.

```bash
npm install
```

![2.2.1](/images/2-deploy-local/2.2/6.png)

2. Next, **start the server**:

```bash
npm run dev
```
![2.2.1](/images/2-deploy-local/2.2/7.png)

3. And the Web Server has successfully started.

#### Deploy Client Application

1. Next, I'll **deploy the client application**:

- Go to the **`frontend`** folder.
- Open the **Terminal** and **install the NPM packages**.

```bash
npm install
```

![2.2.1](/images/2-deploy-local/2.2/8.png)

2. Before running the application, you need to **update the content** of the **vite.config.js** file using the sample configuration below:

```js
/// <reference types="vite/client" />

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  server: {
    proxy: {
      "/api": {
        // API Endpoint của Web Server
        target: "http://localhost:5000/api",
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, ""),
      },
    },
  },
});
```

{{% notice note%}}
The configuration above sets up a proxy for Vite, meaning that when a URL request contains **/api**, it will be replaced by the **target** string.
{{% /notice%}}

3. Run the application:

```bash
npm run dev
```

![2.2.1](/images/2-deploy-local/2.2/9.png)

4. After this section, we'll check the deployment results.

#### Conclusion

From the deployment steps from the beginning of the Local Deployment section to this point, we can draw some conclusions:

- Manual deployment is exhausting, requiring a lot of installations. In the next section, we will use Linux and Docker to deploy the entire application.
- If the application is developed and deployed on Windows, switching to other platforms may be difficult.
- If we deploy this application to a real environment with this strategy and architecture, the system won't be highly reliable.
- It doesn't ensure the "environment" for the applications. When deploying this way, the applications share the same resources, and with other software on the machine. Sometimes errors from other software or applications may affect our system.
