+++
title = "Kiểm tra ứng dụng"
date = 2024
weight = 5
chapter = false
pre = "<b>2.3. </b>"
+++

#### Kiểm tra kết quả triển khai
**ℹ️ Thông tin**: Trước khi truy cập http://localhost:5173/, hãy đảm bảo lệnh `npm run dev` đang chạy trong cả hai **thư mục frontend và backend**.

1. Chúng ta cần truy cập vào URL: `http://localhost:5173`. Lúc này, bạn sẽ thấy giao diện như sau:

!(/images/2-deploy-local/2.3/1.png)

#### Xác thực người dùng

**🔒 Lưu ý bảo mật**: Sử dụng một trong các tài khoản sau để đăng nhập vào ứng dụng:

- User: email `user@example.com`; password `123456`.
- Admin: email `admin@example.com`; password `123456`.

**⚠️ Cảnh báo**: Trong môi trường production thực tế, bạn nên sử dụng AWS IAM Identity Center hoặc Amazon Cognito để việc xác thực bảo mật hơn.

#### Kiểm tra giao diện

1. Sau khi đăng nhập thành công với **admin account**, bạn sẽ thấy nội dung sau trên trang web:
!(/images/2-deploy-local/2.3/2.png)

**💡 Mẹo**: Hãy xem qua một số trang khác để kiểm tra tính năng điều hướng và hiển thị, chẳng hạn như **các trang Users và Clients**:

!(/images/2-deploy-local/2.3/3.png)

!(/images/2-deploy-local/2.3/4.png)
