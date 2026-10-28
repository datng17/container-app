+++
title = "Giới thiệu"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Tổng quan

![1.1](/images/1-introduction/1.2.png)

Trong workshop này, chúng ta sẽ cùng nhau thực hành việc triển khai ứng dụng lên Docker Container, từ xây dựng đến quản lý toàn bộ quá trình vận hành. Bạn sẽ được khám phá cách tận dụng sức mạnh của các công cụ và dịch vụ phổ biến trong môi trường container hóa như Docker Hub, Nginx, Amazon ECR, Amazon RDS, và Amazon EC2.

Những dịch vụ được sử dụng trong workshop bao gồm:

- **Docker Hub**: Đây là dịch vụ lưu trữ Docker image phổ biến nhất, giúp bạn dễ dàng lưu trữ và chia sẻ các image của ứng dụng, từ đó triển khai nhanh chóng ở bất kỳ đâu.

- **Nginx**: Một trong những web server mạnh mẽ nhất, thường được sử dụng như một reverse proxy và load balancer, giúp tối ưu hóa việc phân phối ứng dụng và đảm bảo khả năng mở rộng cao.

- **Amazon Elastic Container Registry (ECR)**: ECR là dịch vụ lưu trữ Docker image an toàn và tích hợp chặt chẽ với các dịch vụ của AWS, giúp bạn quản lý, lưu trữ và triển khai Docker images trực tiếp từ môi trường đám mây.

- **Amazon Relational Database Service (RDS)**: RDS là một dịch vụ cơ sở dữ liệu được quản lý hoàn toàn, giúp tự động hóa các tác vụ bảo trì và tối ưu hóa cơ sở dữ liệu. Trong workshop này, bạn sẽ học cách tích hợp ứng dụng Docker của mình với RDS, đảm bảo hiệu suất cao và bảo mật tốt.

- **Amazon EC2**: EC2 cung cấp máy chủ đám mây linh hoạt và mạnh mẽ để bạn triển khai, chạy container và quản lý các ứng dụng container hóa của mình trên cơ sở hạ tầng AWS.

#### Mô tả tiến trình

1. **Yêu cầu từ người dùng (Client-Side)**:

- **Người dùng** bắt đầu yêu cầu từ trình duyệt hoặc thiết bị của họ, chẳng hạn như truy cập một trang web hoặc ứng dụng.
- Yêu cầu này sẽ được chuyển qua **Internet**, bắt đầu hành trình đến hạ tầng ứng dụng của bạn.

2. **Internet Gateway (Hạ tầng AWS)**:

- Yêu cầu đầu tiên sẽ đi qua **Internet Gateway** trong hạ tầng đám mây của bạn, thường được lưu trữ trên AWS. Internet Gateway đóng vai trò là cầu nối giữa internet công cộng và Virtual Private Cloud (VPC) của bạn.
- Nó chuyển tiếp lưu lượng đến máy chủ Nginx trong cơ sở hạ tầng của bạn.

3. **Nginx (Proxy ngược & Cân bằng tải)**:

- **Nginx** nhận yêu cầu và hoạt động như một **reverse proxy** để điều hướng lưu lượng đến các container ứng dụng thích hợp.
- Nginx chịu trách nhiệm chuyển tiếp yêu cầu đến **container Frontend** (xử lý giao diện người dùng và logic phía client) hoặc **container Backend** (xử lý logic và tương tác với cơ sở dữ liệu).

4. **Container Frontend và Backend**:

- **Container Frontend** (thường được xây dựng với các framework như React, Vue.js, v.v.) xử lý giao diện người dùng và tầng trình bày của ứng dụng. Nó gửi các yêu cầu tới backend để xử lý logic phía máy chủ hoặc truy xuất dữ liệu.
- **Container Backend** (thường được xây dựng với Node.js, Python, v.v.) xử lý yêu cầu, áp dụng logic nghiệp vụ và gọi cơ sở dữ liệu để truy xuất hoặc lưu trữ dữ liệu.

5. **Amazon RDS (Tầng cơ sở dữ liệu)**:

- **Container backend** giao tiếp với **Amazon RDS** (Relational Database Service), nơi dữ liệu của ứng dụng được lưu trữ.
- Backend sẽ lấy dữ liệu cần thiết từ RDS, chẳng hạn như thông tin người dùng, kết quả quiz hoặc bất kỳ tương tác cơ sở dữ liệu nào mà ứng dụng yêu cầu.

6. **Phản hồi tới người dùng**:

- Sau khi backend lấy dữ liệu từ RDS và xử lý yêu cầu, nó gửi phản hồi trở lại **container frontend** thông qua Nginx.
- Frontend hiển thị phản hồi và gửi lại cho **người dùng**, hoàn thành chu kỳ.

7. **Đẩy Docker Images lên Docker Hub và Amazon ECR**:

- Tách biệt với chu kỳ yêu cầu-phản hồi, khi bạn thực hiện thay đổi ứng dụng hoặc hạ tầng, các **Docker images** được cập nhật (cho cả frontend và backend) sẽ được **đẩy** lên **Docker Hub** hoặc **Amazon ECR** (Elastic Container Registry).
- Các kho lưu trữ này lưu trữ hình ảnh một cách an toàn, giúp dễ dàng triển khai lại trên các môi trường khác nhau, chẳng hạn như EC2.
