---
title: "Event 1"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# **Vietnam Cloud Day 2025 :**

# **Ho Chi Minh City Connect Edition for Builders \- GenAI and Data Track**

**Địa điểm**: AWS Event Hall, L26 Bitexco Tower, HCMC

**Thời gian**: Thứ Năm, ngày 18 tháng 09 năm 2025

# Bài thu hoạch “Vietnam Cloud Day 2025: GenAI and Data Track”

### Mục Đích Của Sự Kiện

- Cung cấp cái nhìn tổng quan về **(Agentic AI)** và tầm nhìn chiến lược của AWS.
- Tìm hiểu cách xây dựng **Nền tảng dữ liệu đồng nhất** (Unified Data Foundation) nhằm hỗ trợ hiệu quả cho các hoạt động AI và Phân tích Dữ liệu (Analytics) trên AWS.
- Phân tích chi tiết lộ trình triển khai GenAI, các mô hình **Kiến trúc AI Agent** và những khó khăn trong việc đưa chúng vào môi trường sản xuất (production).
- Nghiên cứu về mô hình **Chu trình Phát triển Hướng Dẫn bởi AI (AI-Driven Development Lifecycle - AI-DLC)**.
- Nắm vững các nguyên tắc cốt lõi về **Bảo mật, Quản trị Rủi ro và AI có Trách nhiệm (Responsible AI)** trong lĩnh vực Generative AI.
- Giới thiệu các **Dịch vụ AWS mới** được thiết kế để hỗ trợ AI Agents và tối đa hóa năng suất làm việc cho doanh nghiệp.

---

### Danh Sách Diễn Giả

- **Jun Kai Loke** - Chuyên gia Kiến trúc Giải pháp AI/ML, AWS
- **Kien Nguyen** - Kiến trúc sư Giải pháp, AWS
- **Tamelly Lim** - Chuyên gia Kiến trúc Giải pháp Lưu trữ, AWS
- **Binh Tran** - Kiến trúc sư Giải pháp Cấp cao, AWS
- **Taiki Dang** - Kiến trúc sư Giải pháp, AWS
- **Christal Poon** - Chuyên gia Kiến trúc Giải pháp, AWS

---

### Nội Dung Nổi Bật

#### Tổng quan về AI Tác Tử (Agentic AI) – Jun Kai Loke

- **Agentic AI** là một xu hướng chiến lược quan trọng, tập trung vào việc tạo ra các hệ thống có khả năng tự vận hành, giảm thiểu sự can thiệp của con người và tự động hóa các quy trình phức tạp ở mức độ sâu.
- Các ví dụ thực tế về việc áp dụng thành công: Katalon, Apero, Techcom Securities.
- **Amazon Bedrock** đóng vai trò là nền tảng cốt lõi để phát triển AI, hỗ trợ:
  - Triển khai bảo mật ở quy mô lớn.
  - Tích hợp các công cụ (tools) và khả năng ghi nhớ (memory).
  - Giám sát toàn diện từ đầu đến cuối (end-to-end monitoring).

#### Xây dựng Nền tảng Dữ liệu Thống nhất trên AWS – Kien Nguyen

- **Thách thức hiện tại**: Nhiều doanh nghiệp gặp khó khăn trong triển khai GenAI do nền tảng dữ liệu chưa sẵn sàng (chỉ 52% CDO đánh giá nền tảng dữ liệu đã sẵn sàng, theo HBR), chủ yếu do dữ liệu bị cô lập (data silos), đội ngũ bị chia rẽ (people silos) và các phân khu kinh doanh riêng biệt (business silos).
- **Chiến lược dữ liệu toàn diện (End-to-End)** bao gồm ba thành phần tương tác: **Nhà sản xuất dữ liệu (Producers)**, **Nền tảng cốt lõi (Foundations)** và **Người tiêu thụ dữ liệu (Consumers)**.
- **Các dịch vụ dữ liệu trọng yếu của AWS**:
  - **Amazon Bedrock** (nền tảng GenAI).
  - **Cơ sở dữ liệu** (RDS và các dịch vụ chuyên dụng hỗ trợ tìm kiếm vector).
  - **Analytics & ML** (SageMaker, Unified Studio).
  - **Quản trị Dữ liệu và AI (Data & AI Governance)**.
  - **Kiến trúc Lake House** (S3, Redshift Managed Storage, Iceberg Open API).
  - **Amazon DataZone** (Quản lý và chia sẻ dữ liệu).

#### Lộ trình GenAI & Kiến trúc AI Agents – Jun Kai Loke & Tamelly Lim

- Bản thiết kế (Blueprint) xây dựng AI Agents gồm: Mô hình (Model) & năng lực ứng dụng (application capabilities), và khung công cụ (tool framework).
- AWS giới thiệu **Amazon Bedrock AgentCore** để khắc phục các khó khăn khi đưa Agents vào môi trường sản xuất.
- **AgentCore** bao gồm: Agent Core Runtime, Agent Core Gateway, Memory, Agent Browser và Code Interpreter, nhằm mục đích tăng cường **bảo mật** và **khả năng mở rộng**.

#### Chu trình Phát triển Hướng Dẫn bởi AI (AI-DLC) – Binh Tran

AI-DLC là mô hình phát triển phần mềm mới, được tự động hóa tối đa bởi AI, gồm 3 giai đoạn:

1.  **Khởi tạo (Inception)**: Xác định bối cảnh (context), phác thảo yêu cầu người dùng (user stories), và lên kế hoạch bằng các đơn vị công việc (work units).
2.  **Xây dựng (Construction)**: Viết mã (Code) + kiểm thử (test), bổ sung kiến trúc, triển khai Cơ sở hạ tầng dưới dạng Mã (IaC) và kiểm thử.
3.  **Vận hành (Operation)**: Triển khai lên môi trường production bằng IaC và quản lý sự cố.

#### Bảo mật Ứng dụng Generative AI – Taiki Dang

- **Các yếu tố bảo mật thiết yếu**: Tuân thủ & Quản trị (Compliance & Governance), Pháp lý & Quyền riêng tư (Legal & Privacy), Các Biện pháp kiểm soát (Controls), Quản lý rủi ro (Risk Management) và Khả năng phục hồi (Resilience).
- **Phân tích Rủi ro theo Lớp**: Rủi ro đối với người dùng cuối (Hallucination, IP, Legal), rủi ro đối với người tinh chỉnh mô hình (data retention) và rủi ro đối với nhà cung cấp mô hình (training data, model construction).
- **Chiến lược Giảm thiểu rủi ro**: Sử dụng Prompt engineering, Fine-tuning, Kỹ thuật Tăng cường Truy xuất (RAG), điều chỉnh tham số, **Bedrock Guardrails** và bảo mật đầu vào (prompt security).
- Cần áp dụng các tiêu chuẩn như AWS Well-Architected, MITRE ATLAS, OWASP Top 10 for LLM Apps, NIST AI 600-1, ISO 42001 và EU AI Act.

#### AI Agents: Tăng cường Năng suất Doanh nghiệp – Christal Poon

- Giới thiệu các dạng AI Agents: Agents chuyên biệt (Specialized Agents), Agents được quản lý hoàn toàn (Fully-managed Agents) và Agents tự xây dựng (DIY Agents).
- Các dịch vụ hỗ trợ năng suất: **Amazon QuickSight** (cho phân tích kinh doanh) và **Amazon Q** (cung cấp Dashboards, Reports, Executive summaries và các Kịch bản AI Agent).

---

### Những Gì Học Được

#### Tư Duy & Chiến Lược

- **Agentic AI** là bước phát triển tiếp theo của tự động hóa, hướng tới các hệ thống tự chủ, giảm sự giám sát của con người.
- **Nền tảng dữ liệu vững chắc** (dựa trên S3, Lake House, Bedrock, SageMaker) là yêu cầu tiên quyết để triển khai GenAI thành công.
- **AI-DLC** cung cấp một phương pháp luận hiện đại, tự động hóa toàn bộ chu trình phát triển từ lập kế hoạch, viết code, kiểm thử đến triển khai.

#### Kiến Trúc & Kỹ Thuật

- Nắm bắt được kiến trúc **AI Agents** và giải pháp **Amazon Bedrock AgentCore** giúp giải quyết các thách thức về bảo mật và khả năng mở rộng trong môi trường sản xuất.
- **Bảo mật** phải được tích hợp ở mọi cấp độ của AI stack, từ dữ liệu, mô hình đến ứng dụng đầu cuối, đồng thời tuân thủ các chuẩn mực và quy định quốc tế.

#### Ứng Dụng Công Nghệ

- AWS đang đầu tư và mở rộng mạnh mẽ hệ sinh thái **AI Agents & Enterprise AI** thông qua các dịch vụ như Amazon Q và QuickSuite (sắp ra mắt).

---

### Ứng Dụng Vào Công Việc

- **Tối ưu hóa quy trình**: Nghiên cứu và tích hợp các **AI Agents** vào các tác vụ nghiệp vụ có tính lặp lại để tăng hiệu suất.
- **Quản lý chất lượng**: Sử dụng **Amazon Bedrock, Amazon Q và Guardrails** để kiểm soát chất lượng, tính an toàn và giảm thiểu hiện tượng "hallucination" của mô hình.
- **Xây dựng hạ tầng**: Đảm bảo xây dựng một **nền tảng dữ liệu thống nhất** và có quản trị rõ ràng trước khi triển khai các dự án GenAI.
- **Áp dụng AI-DLC**: Thử nghiệm áp dụng mô hình phát triển phần mềm **AI-DLC** vào các dự án nội bộ để tăng tốc độ triển khai.
- **Phân tích nghiệp vụ**: Sử dụng **QuickSight và Amazon Q** để tạo nhanh các dashboard và insight phục vụ ban lãnh đạo và đội ngũ nghiệp vụ.

---

### Trải nghiệm trong event

Workshop đã mang lại cái nhìn rõ ràng và thực tế về sự chuyển đổi từ tự động hóa truyền thống sang kỷ nguyên **Agentic AI**. Các bài trình bày của diễn giả đã định hướng cụ thể cho hành trình áp dụng GenAI tại Việt Nam. Sự kết hợp giữa **AgentCore, Bedrock, AI-DLC và Amazon Q** đã phác họa nên một bức tranh toàn diện và mạnh mẽ về thế hệ AI tiếp theo dành cho doanh nghiệp, từ nền tảng dữ liệu, phát triển ứng dụng, đến bảo mật và vận hành.

- Thêm các hình ảnh của các bạn tại đây

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật chuyên sâu mà còn giúp thay đổi tư duy về cách tích hợp AI một cách chiến lược, có trách nhiệm và an toàn vào mọi khía cạnh của doanh nghiệp.
