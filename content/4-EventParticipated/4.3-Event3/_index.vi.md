---
title: "Event 3"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Bài thu hoạch “Workshop: Data Science on AWS”

**Địa điểm**: FPT University HCM Campus

**Thời gian**:Thứ Năm, ngày 16 tháng 10 năm 2025

### Mục Đích Của Sự Kiện

- Khám phá toàn bộ hành trình xây dựng một hệ thống Khoa học Dữ liệu (Data Science) hiện đại, từ lý thuyết đến thực hành.
- Nắm vững **Quy trình Data Science đầu-cuối (end-to-end)** trên AWS, bao gồm lưu trữ, xử lý và triển khai mô hình.
- Có được trải nghiệm thực tế với các tập dữ liệu thực tế (IMDb) và các mô hình ứng dụng (Phân tích Cảm xúc - Sentiment Analysis).
- Phân tích sự đánh đổi (trade-offs) về chi phí và hiệu suất giữa cơ sở hạ tầng **Cloud và On-premise**.

---

### Danh Sách Diễn Giả

- **Ông Văn Hoàng Kha** – Kiến trúc sư Giải pháp Đám mây, AWS Community Builder
- **Ông Bạch Doãn Vương** – Kỹ sư Cloud DevOps, AWS Community Builder

---

### Nội Dung Nổi Bật

#### 1. Vai trò của Cloud trong Data Science và Tổng quan Quy trình

- **Tầm quan trọng của Cloud:** Phân tích lý do tại sao khoa học dữ liệu hiện đại cần dựa vào nền tảng đám mây để đạt được khả năng mở rộng (scalability) và tính tích hợp cao, thay vì bị giới hạn bởi cơ sở hạ tầng on-premise truyền thống.
- **Quy trình Data Science trên AWS:**
  - **Lưu trữ (Storage):** Sử dụng **Amazon S3** làm nền tảng hồ dữ liệu (data lake) cốt lõi.
  - **ETL/Xử lý (Processing):** Sử dụng **AWS Glue** cho các tác vụ tích hợp dữ liệu phi máy chủ (serverless data integration).
  - **Mô hình hóa (Modeling):** Tận dụng **Amazon SageMaker** làm trung tâm để xây dựng, huấn luyện và triển khai mô hình.
  - Tổng quan về hệ thống AI/ML rộng lớn của AWS, bao gồm các dịch vụ AI, dịch vụ ML và cơ sở hạ tầng.

#### 2. Minh họa Thực hành (Practical Demos)

- **Demo 1: Xử lý Dữ liệu với AWS Glue:**
  - **Kịch bản:** Xử lý và làm sạch dữ liệu thô từ tập dữ liệu IMDb.
  - **Kỹ thuật:** Trình diễn cách thực hiện kỹ thuật feature engineering và chuẩn bị dữ liệu hiệu quả. Workshop cũng làm nổi bật các phương pháp khác nhau, từ các lựa chọn ít mã (low-code) như **SageMaker Canvas** đến các phương pháp ưu tiên mã (code-first) sử dụng Numpy/Pandas.
- **Demo 2: Phân tích Cảm xúc với SageMaker:**
  - **Kịch bản:** Huấn luyện và triển khai một mô hình học máy để phân tích cảm xúc từ dữ liệu văn bản.
  - **Quy trình:** Minh họa chu trình "Huấn luyện, Tinh chỉnh, Triển khai (Train, Tune, Deploy)" trong **SageMaker Studio**. Phiên này cũng đề cập đến khái niệm "Mang mô hình của riêng bạn (Bring Your Own Model - BYOM)", cho thấy tính linh hoạt với các framework như TensorFlow và PyTorch.

#### 3. Thảo luận Chiến lược

- **Cloud so với On-Premise:** Thảo luận chuyên sâu về tối ưu hóa chi phí và các chỉ số hiệu suất. Nội dung làm nổi bật cách tính đàn hồi của đám mây (cloud elasticity) cho phép thử nghiệm các khối lượng công việc nặng mà không cần đầu tư vốn lớn ban đầu cho phần cứng on-premise.
- **Hướng dẫn Dự án Nhỏ:** Giới thiệu một dự án được thiết kế sau workshop nhằm củng cố các kỹ năng đã học.

---

### Những Gì Học Được

#### Quy trình Kỹ thuật (Technical Workflow)

- **Quy trình Thống nhất:** Một quy trình khoa học dữ liệu mạnh mẽ không chỉ nằm ở mã nguồn; nó đòi hỏi sự tích hợp liền mạch giữa lưu trữ (S3), làm sạch (Glue) và mô hình hóa (SageMaker).
- **Lựa chọn Công cụ:** Việc hiểu rõ khi nào nên sử dụng các dịch vụ được quản lý sẵn (như Amazon Comprehend hoặc Textract) và khi nào nên xây dựng mô hình tùy chỉnh trên SageMaker là yếu tố then chốt để đạt được hiệu quả.

#### Ứng dụng Thực tiễn (Industry Application)

- **Bối cảnh Thực tế:** Sự chuyển đổi từ lý thuyết học thuật sang ứng dụng công nghiệp nằm ở khả năng tự động hóa và mở rộng quy mô.
- **Nhận thức về Chi phí:** Các dự án dữ liệu thành công phải cân bằng giữa độ chính xác của mô hình và chi phí tính toán liên quan.

---

### Ứng Dụng Vào Công Việc

- **Áp dụng AWS Glue:** Đề xuất chuyển đổi các tập lệnh ETL cục bộ sang AWS Glue để tự động hóa, xử lý dữ liệu phi máy chủ trên các tập dữ liệu lớn hơn.
- **Triển khai SageMaker:** Di chuyển các mô hình thử nghiệm từ các sổ ghi chép Jupyter (Jupyter notebooks) cục bộ sang **SageMaker Studio** để chuẩn hóa quy trình huấn luyện và triển khai.
- **Thực hiện Dự án:** Thực hiện dự án nhỏ được đề xuất sau workshop để củng cố sự hiểu biết về quy trình xử lý dữ liệu IMDb.

---

### Trải nghiệm trong event

Workshop **“Data Science on AWS”** đóng vai trò là cầu nối quan trọng giữa kiến thức học thuật và thực tiễn doanh nghiệp.

- **Kết nối Trực tiếp:** Sự kiện đã liên kết kiến thức lý thuyết với các công nghệ đang được sử dụng bởi các doanh nghiệp hàng đầu thế giới.
- **Góc nhìn Thực tiễn:** Việc quan sát quá trình làm sạch **tập dữ liệu IMDb** và triển khai **mô hình Phân tích Cảm xúc** trực tiếp trên đám mây đã giúp đơn giản hóa sự phức tạp của AI trên nền tảng Cloud.
- **Hướng dẫn Chuyên gia:** Việc tương tác với các AWS Community Builders đã cung cấp những hiểu biết sâu sắc về cuộc tranh luận "Cloud so với On-premise", giúp tôi nắm bắt được giá trị chiến lược của việc di chuyển lên đám mây ngoài các tính năng kỹ thuật.

#### Một số hình ảnh khi tham gia sự kiện

- Thêm các hình ảnh của các bạn tại đây

> Tổng thể, workshop đã cung cấp một khuôn khổ Data Science toàn diện, nhấn mạnh tầm quan trọng của các công cụ AWS được quản lý để đạt được tính linh hoạt, khả năng mở rộng và tối ưu hóa chi phí.
