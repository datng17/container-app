+++
title = "Triển khai trên Local"
date = 2024
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

Để có thể hiểu được vì sao mà chúng ta nên triển khai ứng dụng trên Docker Container với Docker làm nền tảng thay vì là nền tảng của chính nền tảng trên máy vi tính cá nhân.

Để ứng dụng của người dùng cuối có thể hoạt động được (như là người dùng có thể thêm thông tin, sửa thông tin, ...) thì chúng ta cần phải có một hoặc nhiều server để chịu trách nhiệm xử lý các yêu cầu từ người dùng. Khi này thì một hoặc nhiều server sẽ sử dụng tới tài nguyên của máy chủ (Host).

Trong phần này thì chúng ta sẽ tiến hành triển khai một ứng dụng mẫu ở trên chính máy vi tính cá nhân để quan sát và đánh giá.

![local_architect](/images/2-deploy-local/arc.png)
