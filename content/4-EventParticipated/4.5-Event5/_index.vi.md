---
title: "Event 5"
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

# **AWS Mastery 2: AWS DevOps & Modern Operations**

**Địa điểm**: AWS Event Hall, L26 Bitexco Tower, HCMC

**Thời gian**:Thứ Hai, ngày 17 tháng 11 năm 2025

# Bài thu hoạch “AWS DevOps & Modern Operations"

### Mục Đích Của Sự Kiện

- Xây dựng tư duy **DevOps** và nắm vững cách thức đo lường hiệu suất thông qua các chỉ số quan trọng **DORA metrics**.
- Thiết lập quy trình **CI/CD** hoàn chỉnh, tự động hóa bằng cách sử dụng bộ công cụ **AWS Developer Tools**.
- Hiện đại hóa việc quản lý cơ sở hạ tầng bằng mã (**Infrastructure as Code - IaC**) với **CloudFormation** và **CDK**.
- Triển khai các ứng dụng được đóng gói trong container (Docker) trên các dịch vụ như **ECS, EKS** và **App Runner**.
- Xây dựng hệ thống **Khả năng quan sát (Observability)** toàn diện cho các ứng dụng phân tán.

---

### Danh Sách Diễn Giả

- **Đội ngũ chuyên gia AWS (AWS Experts)** (Các chuyên gia chuyên sâu về DevOps, Container và Observability)

---

### Nội Dung Nổi Bật

#### Tư duy DevOps & CI/CD

- **DORA Metrics:** Nhấn mạnh tầm quan trọng của các chỉ số hiệu suất như Tần suất triển khai (Deployment Frequency), Thời gian thay đổi (Lead Time for Changes) và Thời gian trung bình để phục hồi (MTTR - Mean Time to Recover).
- **Chiến lược Git:** So sánh các chiến lược quản lý mã nguồn như GitFlow và Trunk-based development.
- **Tự động hóa Pipeline:** Minh họa quy trình CI/CD đầy đủ: từ **CodeCommit** (lưu trữ mã), **CodeBuild** (xây dựng/kiểm thử), đến **CodeDeploy** (triển khai) được điều phối bởi **CodePipeline**.
- **Chiến lược Triển khai:** Giới thiệu các kỹ thuật triển khai an toàn nhằm giảm thiểu rủi ro: Blue/Green, Canary và Rolling updates.

#### Cơ sở hạ tầng dưới dạng Mã (Infrastructure as Code - IaC)

- **CloudFormation:** Hướng dẫn quản lý hạ tầng bằng template, bao gồm khái niệm Stacks và cơ chế phát hiện sai lệch (Drift detection).
- **AWS CDK:** Sử dụng ngôn ngữ lập trình phổ biến để định nghĩa hạ tầng, tận dụng các "Constructs" và các mẫu thiết kế có thể tái sử dụng.
- **Lựa chọn IaC:** Thảo luận về các tiêu chí để lựa chọn giữa CloudFormation và CDK tùy thuộc vào yêu cầu và quy mô của dự án.

#### Các Dịch vụ Container

- **Phổ rộng Tính toán (Spectrum of Compute):** Từ quản lý hình ảnh (image management) bằng **ECR** đến các tùy chọn điều phối (orchestration): **ECS** (đơn giản, tích hợp AWS sâu), **EKS** (chuẩn Kubernetes mở) và **App Runner** (giải pháp đơn giản hóa tối đa cho web apps/API).
- **Triển khai Microservices:** So sánh và trình diễn cách triển khai các dịch vụ nhỏ (microservices) trên các nền tảng khác nhau.

#### Giám sát & Khả năng Quan sát (Monitoring & Observability)

- **Observability Toàn diện:** Kết hợp **CloudWatch** (để thu thập Metrics, Logs, Alarms) và **X-Ray** (cho Distributed Tracing - truy vết lỗi ứng dụng phân tán) để có cái nhìn sâu sắc và toàn diện về tình trạng hệ thống.
- **Thực hành Tốt nhất:** Thiết lập Dashboard giám sát trực quan và quy trình trực chiến (On-call) hiệu quả.

---

### Những Gì Học Được

#### Ưu tiên Tự động hóa (Automation First)

- **CI/CD** là nền tảng văn hóa giúp giảm thiểu lỗi do con người và tăng tốc độ phát hành sản phẩm.
- **IaC** là tiêu chuẩn bắt buộc cho mọi cơ sở hạ tầng hiện đại, đảm bảo môi trường Phát triển/Kiểm thử/Sản xuất (Dev/Test/Prod) luôn đồng nhất và có thể tái tạo.

#### Vận hành Xuất sắc (Operational Excellence)

- **Khả năng Quan sát (Observability)** quan trọng hơn Giám sát (Monitoring) đơn thuần, đặc biệt trong kiến trúc Microservices, vì nó cho phép truy vết nguyên nhân lỗi một cách nhanh chóng (tracing).
- Việc lựa chọn chiến lược triển khai phù hợp (như Blue/Green) là chìa khóa để đạt được thời gian ngừng hoạt động (Downtime) gần như bằng không.

---

### Ứng Dụng Vào Công Việc

- **Tái cấu trúc Pipeline:** Chuyển đổi các quy trình build thủ công hiện tại sang **AWS CodePipeline** tích hợp các bước kiểm thử tự động.
- **Áp dụng CDK:** Bắt đầu sử dụng **AWS CDK** để định nghĩa cơ sở hạ tầng cho các dự án mới, từ bỏ thói quen thao tác trực tiếp trên Console.
- **Container hóa:** Đóng gói các ứng dụng vào Docker và thử nghiệm triển khai chúng lên **AWS App Runner** đối với các dịch vụ nhỏ hơn.
- **Thiết lập Truy vết:** Tích hợp **AWS X-Ray** vào ứng dụng để theo dõi độ trễ (latency) và luồng giao tiếp giữa các microservices.

---

### Trải nghiệm trong event

Sự kiện đã hệ thống hóa kiến thức một cách liền mạch, đi từ định hình tư duy (Mindset) đến giới thiệu các công cụ (Tools) và quy trình vận hành (Operations).

#### Quy trình Tích hợp

- Phần demo **"Full CI/CD pipeline walkthrough"** rất ấn tượng, giúp tôi hình dung rõ ràng toàn bộ hành trình của mã nguồn từ máy lập trình viên đến môi trường Production.
- Tôi đã hiểu rõ sự khác biệt và các trường hợp sử dụng cụ thể của **ECS so với EKS**, giúp tăng sự tự tin khi đề xuất các giải pháp container hóa cho công ty.

#### Tính Thực tiễn Cao

- Các bài học về **Deployment strategies** (như Feature flags, Canary) mang tính ứng dụng thực tế cao, giải quyết được vấn đề "ngại triển khai" của đội ngũ.
- Phần định hướng nghề nghiệp (Career roadmap) cuối giờ cung cấp lộ trình phát triển kỹ năng **DevOps** rõ ràng.

#### Một số hình ảnh khi tham gia sự kiện

- Thêm các hình ảnh của các bạn tại đây

> Tóm lại, buổi workshop đã làm rõ mối liên kết chặt chẽ và không thể tách rời giữa Mã nguồn (Code), Cơ sở hạ tầng (IaC) và Khả năng quan sát (Observability) trong vận hành hiện đại.
