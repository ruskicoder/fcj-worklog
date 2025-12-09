---
title: "Worklog Tuần 4"
date: "2025-09-29"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4

* Tìm hiểu sâu hơn về AWS VPC và các khái niệm networking
* Học về dịch vụ lưu trữ Amazon S3 và các best practices
* Khám phá các dịch vụ database của AWS (RDS)
* Tiếp tục thực hành với các dịch vụ AWS cốt lõi

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| Thứ Hai (30/9) | - Ôn tập các khái niệm EC2 tuần trước<br>&emsp;+ Các loại instance và sizing<br>&emsp;+ Cấu hình security groups<br>- Nghiên cứu tài liệu AWS về VPC cơ bản | 30/09/2025 | 30/09/2025 | [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/) |
| Thứ Ba (1/10) | - Học các khái niệm cơ bản về VPC<br>&emsp;+ Subnets (public vs private)<br>&emsp;+ Route tables<br>&emsp;+ Internet Gateway<br>&emsp;+ NAT Gateway | 01/10/2025 | 01/10/2025 | [AWS VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/) |
| Thứ Tư (2/10) | - Nghiên cứu dịch vụ Amazon S3<br>&emsp;+ Tạo và quản lý bucket<br>&emsp;+ Các khái niệm object storage<br>&emsp;+ Các storage classes của S3<br>&emsp;+ Kiểm soát truy cập và permissions | 02/10/2025 | 02/10/2025 | [AWS S3 Documentation](https://docs.aws.amazon.com/s3/) |
| Thứ Năm (3/10) | - Tiếp tục tìm hiểu sâu về S3<br>&emsp;+ Versioning và lifecycle policies<br>&emsp;+ Các tùy chọn mã hóa S3<br>&emsp;+ Static website hosting | 03/10/2025 | 03/10/2025 | [AWS S3 Best Practices](https://docs.aws.amazon.com/AmazonS3/latest/userguide/best-practices.html) |
| Thứ Sáu (4/10) | - Giới thiệu về AWS RDS<br>&emsp;+ Các tùy chọn database engine<br>&emsp;+ Các loại RDS instance<br>&emsp;+ Khái niệm backup và restore<br>- Ôn tập và củng cố kiến thức tuần | 04/10/2025 | 04/10/2025 | [AWS RDS Documentation](https://docs.aws.amazon.com/rds/) |

### Kết quả đạt được tuần 4

* **Thành thạo VPC Networking**
  * Hiểu kiến trúc VPC và các thành phần
  * Nắm được sự khác biệt giữa public và private subnets
  * Hiểu các khái niệm routing với route tables
  * Hiểu cách hoạt động của Internet Gateway và NAT Gateway

* **Thành thạo Amazon S3**
  * Học các khái niệm lưu trữ S3 và use cases
  * Hiểu các storage classes khác nhau của S3 (Standard, IA, Glacier)
  * Thực hành tạo bucket và quản lý objects
  * Cấu hình bucket policies và access controls
  * Khám phá S3 versioning và lifecycle management
  * Học về các tùy chọn mã hóa S3 (SSE-S3, SSE-KMS)

* **Giới thiệu về Database Services**
  * Có cái nhìn tổng quan về dịch vụ AWS RDS
  * Hiểu các tùy chọn database engine khác nhau (MySQL, PostgreSQL, v.v.)
  * Học về sizing và cấu hình RDS instance
  * Khám phá khả năng backup và restore

* **Phát triển kỹ năng thực hành**
  * Cải thiện hiểu biết về kiến trúc networking của AWS
  * Nâng cao khả năng điều hướng tài liệu AWS hiệu quả
  * Chuẩn bị cho các bài lab thực hành tuần tới

### Các thách thức gặp phải

* Các khái niệm routing trong VPC ban đầu khá phức tạp, đặc biệt là hiểu mối quan hệ giữa route tables, subnets và gateways
* S3 bucket policies và IAM permissions cần chú ý cẩn thận để tránh các vấn đề về quyền truy cập
* Cân bằng giữa học lý thuyết và thời gian thực hành

### Bài học quan trọng

* VPC là nền tảng cho kiến trúc networking và security của AWS
* S3 rất linh hoạt ngoài việc lưu trữ đơn giản - có thể host static websites, làm data lake, v.v.
* Thiết kế subnet phù hợp (public vs private) rất quan trọng cho các best practices về bảo mật
* Tài liệu AWS rất toàn diện nhưng cần thời gian để tiếp thu kỹ lưỡng

### Mục tiêu tuần tới

* Tiếp tục với các dịch vụ database của AWS (thực hành RDS)
* Bắt đầu công việc dịch blog (blog kỹ thuật AWS đầu tiên)
* Khám phá AWS Lambda và các khái niệm serverless
* Tìm hiểu sâu hơn về IAM roles và policies
