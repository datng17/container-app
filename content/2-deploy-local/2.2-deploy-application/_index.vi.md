+++
title = "Triển khai ứng dụng"
date = 2024
weight = 4
chapter = false
pre = "<b>2.2. </b>"
+++

{{% notice note%}}
Để hoàn thành phần này, bạn cần cài đặt **Git** trước đó.
{{% /notice%}}

#### Tải mã nguồn
1. Tạo một thư mục với tên bất kỳ (ví dụ: *workspace*).
2. Nhấp chuột phải và chọn **Open in Terminal**.

![2.2.1](/images/2-deploy-local/2.2/1.png)

3. Clone mã nguồn ứng dụng từ GitHub về máy.

```bash
git clone https://github.com/datng17/fcaj-resbar.git
```

4. Kết quả sau khi clone:

![2.2.1](/images/2-deploy-local/2.2/2.png)

#### Thêm dữ liệu

1. Để thêm dữ liệu:

- Truy cập thư mục **database** trong thư mục mã nguồn đã tải.
- Sao chép đường dẫn từ thanh địa chỉ trên Windows.
- Dán đường dẫn vào MySQL Shell và thêm script `init.sql` vào cuối.

![2.2.1](/images/2-deploy-local/2.2/3.png)

2. Sử dụng MySQL Shell để kết nối tới MySQL Server. Các bước kết nối tương tự phần trước. Trong thư mục project có **database folder** chứa các script SQL để tạo cơ sở dữ liệu, bảng, ràng buộc và thêm dữ liệu. Ở bước này, sử dụng lệnh `source` để chạy script.

![2.2.1](/images/2-deploy-local/2.2/4.png)

3. Chạy một số truy vấn để kiểm tra:

```sql
SELECT * FROM Clients;
```

![2.2.1](/images/2-deploy-local/2.2/5.png)

#### Triển khai Web Server
1. Mở **Terminal** trong **thư mục backend** và tiến hành **install the NPM packages** để chạy server.

```bash
npm install
```

![2.2.1](/images/2-deploy-local/2.2/6.png)

2. Tiếp theo, **start the server**:

```bash
npm run dev
```

![2.2.1](/images/2-deploy-local/2.2/7.png)

3. Web Server đã khởi động thành công.

#### Triển khai client application
1. Tiếp theo, triển khai **client application**:
- Truy cập thư mục **`frontend`**.
- Mở **Terminal** và **cài đặt gói npm**

```bash
npm install
```

![2.2.1](/images/2-deploy-local/2.2/8.png)

2. Trước khi chạy ứng dụng, cần **cập nhật nội dung** trong file **vite.config.js** như cấu hình mẫu dưới đây:

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
Cấu hình trên thiết lập proxy cho Vite, nghĩa là khi URL request chứa **/api** thì sẽ được thay thế bằng chuỗi **target**.
{{% /notice%}}

3. Chạy ứng dụng:

```bash
npm run dev
```

![2.2.1](/images/2-deploy-local/2.2/9.png)

4. Sau phần này, chúng ta sẽ kiểm tra kết quả triển khai.

#### Kết luận

Từ các bước triển khai trong phần Local Deployment đến đây, có thể rút ra một số kết luận:

- Triển khai thủ công khá tốn công sức, yêu cầu cài đặt nhiều thành phần. Ở phần tiếp theo, chúng ta sẽ sử dụng Linux và Docker để triển khai toàn bộ ứng dụng.
- Nếu ứng dụng được phát triển và triển khai trên Windows, việc chuyển sang nền tảng khác có thể gặp khó khăn.
- Nếu triển khai ứng dụng này vào môi trường thực tế với kiến trúc hiện tại, hệ thống sẽ không có độ tin cậy cao.
- Không đảm bảo tính nhất quán của môi trường. Khi triển khai theo cách này, các ứng dụng dùng chung tài nguyên với các phần mềm khác trên máy, dễ gây xung đột và lỗi ngoài ý muốn.