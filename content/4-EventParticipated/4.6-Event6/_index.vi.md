---
title: "Event 6"
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

# **AWS Cloud Mastery Series #3: Security (AWS Well-Architected Security Pillar)**

**Địa điểm**: AWS Event Hall, L26 Bitexco Tower, HCMC

**Thời gian**: Thứ Bảy, ngày 29 tháng 11 năm 2025

# Bài thu hoạch "AWS Cloud Mastery Series #3: Security"

### Mục Đích Của Sự Kiện

- Hiểu sâu về vai trò của **Trụ cột Bảo mật (Security Pillar)** trong Khung kiến trúc Well-Architected của AWS.
- Nắm vững **5 Trụ cột Bảo mật** cốt lõi: Quản lý Định danh (IAM), Phát hiện (Detection), Bảo mật Hạ tầng (Infrastructure), Bảo vệ Dữ liệu (Data Protection), và Phản ứng Sự cố (Incident Response).
- Cập nhật các mối đe dọa an ninh mạng hàng đầu đang tồn tại trong môi trường Cloud tại thị trường Việt Nam.
- Thực hành các kỹ năng như rà soát quyền hạn (IAM) và xây dựng quy trình phản ứng sự cố (**IR Playbook**).

---

### Danh Sách Diễn Giả

- **Đội ngũ chuyên gia bảo mật AWS (AWS Security Experts)** (Chuyên sâu về kiến trúc bảo mật và tuân thủ)

---

### Nội Dung Nổi Bật

#### Nền tảng & Định danh (Trụ cột 1)

- **Nguyên tắc Cốt lõi:** Yêu cầu áp dụng nghiêm ngặt các nguyên tắc **Đặc quyền Tối thiểu (Least Privilege)**, **Zero Trust** (Không tin tưởng mặc định), và **Bảo mật Nhiều lớp (Defense in Depth)**.
- **IAM Hiện đại:** Chuyển đổi từ việc sử dụng IAM Users (với thông tin xác thực dài hạn) sang sử dụng **IAM Roles** và **AWS Identity Center (SSO)** để quản lý truy cập tập trung.
- **Kiểm soát Truy cập:** Sử dụng **Service Control Policies (SCP)** và **Permission Boundaries** để giới hạn phạm vi quyền hạn trong các môi trường đa tài khoản (multi-account).
- **Demo Thực hành Nhỏ:** Trình diễn cách xác thực (Validate) Chính sách IAM và mô phỏng quyền truy cập để phát hiện các lỗi cấu hình bảo mật.

#### Phát hiện & Hạ tầng (Trụ cột 2 & 3)

- **Giám sát Liên tục:** Kích hoạt các dịch vụ như **CloudTrail** (ở cấp độ toàn tổ chức), **GuardDuty** và **Security Hub** để giám sát và đánh giá bảo mật không ngừng nghỉ.
- **Chiến lược Ghi nhật ký:** Yêu cầu ghi lại nhật ký ở mọi tầng của hệ thống: VPC Flow Logs (mạng), ALB logs (ứng dụng) và S3 logs (lưu trữ).
- **Bảo mật Mạng:** Thực hiện phân đoạn mạng (Segmentation) với VPC, kết hợp sử dụng **Security Groups** và **NACLs**. Bảo vệ khu vực biên bằng **WAF, Shield** và **Network Firewall**.

#### Bảo vệ Dữ liệu & Phản ứng Sự cố (Trụ cột 4 & 5)

- **Mã hóa:** Thực hiện mã hóa dữ liệu trong quá trình truyền tải (in-transit) và dữ liệu đang lưu trữ (at-rest) trên các dịch vụ như S3, EBS, RDS, sử dụng dịch vụ **KMS (Key Management Service)**.
- **Quản lý Bí mật:** Loại bỏ việc mã hóa cứng (hard-code) thông tin xác thực bằng cách sử dụng **Secrets Manager** và **Parameter Store**, kết hợp cơ chế xoay vòng (rotation) tự động.
- **Tự động hóa Phản ứng Sự cố:** Xây dựng các kịch bản phản ứng (**Playbook**) cho các sự cố thường gặp (như lộ khóa truy cập, mã độc) và tự động hóa quy trình cô lập tài nguyên bị ảnh hưởng bằng **Lambda/Step Functions**.

---

### Những Gì Học Được

#### Tư duy Zero Trust

- **Định danh là Hàng rào:** Trong môi trường Cloud, **Định danh (Identity)** đã trở thành rào cản bảo vệ quan trọng nhất, thay thế cho địa chỉ IP truyền thống.
- Luôn tuân thủ nguyên tắc: Không bao giờ tin tưởng mặc định, phải luôn xác thực mọi yêu cầu và chỉ cấp quyền tối thiểu cần thiết.

#### Tự động hóa là Cốt lõi (Automation is Key)

- Bảo mật thủ công không thể theo kịp tốc độ triển khai của Cloud. Cần phải áp dụng các phương pháp như **Detection-as-Code** và **Auto-remediation** (tự động khắc phục) để giảm thiểu rủi ro do lỗi con người và sự chậm trễ.

---

### Ứng Dụng Vào Công Việc

- **Kiểm tra IAM:** Rà soát lại toàn bộ IAM User, xóa bỏ các khóa truy cập cũ (old keys) và chuyển đổi các ứng dụng sang sử dụng **IAM Role** để tăng cường bảo mật.
- **Kích hoạt GuardDuty:** Bật dịch vụ **GuardDuty** trên tất cả các khu vực (region) và tài khoản để phát hiện sớm các hành vi truy cập và hoạt động bất thường.
- **Triển khai Secrets Manager:** Thay thế các tệp cấu hình (config file) chứa mật khẩu cơ sở dữ liệu bằng cách sử dụng lời gọi API tới **Secrets Manager**.
- **Xây dựng IR Playbook:** Viết quy trình xử lý sự cố chi tiết cho tình huống "IAM Key bị lộ" và thực hiện diễn tập với đội ngũ kỹ thuật.

---

### Trải nghiệm trong event

Buổi workshop đi sâu vào chi tiết kỹ thuật, bao phủ toàn diện các khía cạnh bảo mật thiết yếu mà một kỹ sư Cloud hiện đại cần phải nắm vững.

#### Khung làm việc Toàn diện

- Việc chia nội dung theo **5 Trụ cột Bảo mật** đã giúp tôi hệ thống hóa lại các kiến thức bảo mật vốn rời rạc trước đây thành một khung chuẩn chỉnh, dễ áp dụng.
- Phần thảo luận về **Các mối đe dọa hàng đầu tại Việt Nam** mang tính thực tế cao, giúp đội ngũ nhận diện được các rủi ro cụ thể phù hợp với bối cảnh trong nước.

#### Thực hành Ứng dụng

- Các demo về **Access Analyzer** và công cụ **Validate IAM Policy** rất hữu ích, trực tiếp giải quyết được khó khăn hàng ngày khi gỡ lỗi quyền hạn (permissions).
- Phần **Incident Response** đã làm rõ rằng "phát hiện" (detection) chỉ là một phần, "phản ứng" (response) tự động và nhanh chóng mới là yếu tố quyết định sự an toàn của hệ thống.

#### Một số hình ảnh khi tham gia sự kiện

- Thêm các hình ảnh của các bạn tại đây

> Tổng thể, sự kiện đã khẳng định rõ ràng rằng bảo mật không phải là rào cản (blocker) mà là yếu tố cho phép doanh nghiệp vận hành nhanh hơn và an toàn hơn (**enabler**).
