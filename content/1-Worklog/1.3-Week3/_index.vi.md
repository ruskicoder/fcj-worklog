---
title: "Worklog Tuần 3"
date: "2025-09-22"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---


### Mục tiêu tuần 3:

* Khám phá và hiểu các khái niệm cơ bản về VPC (Virtual Private Cloud)
* Học các kiến thức cơ bản về dịch vụ EC2 và thực hành triển khai
* Triển khai website tĩnh sử dụng S3 và EC2
* Thực hành vẽ sơ đồ kiến trúc AWS với draw.io
* Hiểu các chiến lược tối ưu hóa chi phí trong AWS

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Khám phá các khái niệm và kiến trúc VPC <br> - Thực hành mở và cấu hình VPC instances <br> - Học vẽ sơ đồ kiến trúc AWS sử dụng draw.io                                                  | 22/09/2025   | 22/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 2   | - Thử phát triển ứng dụng website tĩnh sử dụng Kiro AI <br> - Khắc phục các vấn đề triển khai <br> - Học về việc xác định yêu cầu rõ ràng cho phát triển hỗ trợ bởi AI                      | 23/09/2025   | 23/09/2025      |                                           |
| 3   | - Thực hành tích hợp VPC với S3 <br> - Triển khai website tĩnh đơn giản sử dụng S3 <br> - Cấu hình S3 bucket để host website tĩnh                                                          | 24/09/2025   | 24/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Cấu hình EC2 instance để host server <br> - Khám phá chức năng và tính năng của dịch vụ EC2 <br> - Tìm hiểu các chiến lược tối ưu hóa chi phí AWS <br> - Demo khả năng của dịch vụ EC2   | 25/09/2025   | 25/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Ôn tập các nguyên tắc Quản lý Chi phí AWS <br> - Xem lại các module S3, VPC và EC2 <br> - Kiểm tra triển khai và chức năng của website tĩnh                                               | 26/09/2025   | 26/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Thực hành vẽ sơ đồ kiến trúc AWS với draw.io <br> - Xem video khóa học AWS Study Group trên YouTube <br> - Củng cố kiến thức đã học trong tuần                                            | 27/09/2025   | 27/09/2025      | Kênh YouTube AWS Study Group              |


### Kết quả đạt được tuần 3:

* **Kiến thức cơ bản về VPC:**
  * Hiểu kiến trúc VPC và các khái niệm cốt lõi
  * Cấu hình thành công các VPC instances
  * Học cấu hình mạng VPC và security groups
  * Thực hành tích hợp VPC với các dịch vụ AWS khác

* **Thành thạo dịch vụ EC2:**
  * Có kinh nghiệm thực tế với triển khai EC2 instance
  * Khám phá các loại và cấu hình EC2 instance
  * Học các phương pháp kết nối và quản lý EC2
  * Hiểu tích hợp EC2 với VPC

* **Triển khai Website Tĩnh:**
  * Triển khai thành công website tĩnh sử dụng S3
  * Cấu hình S3 bucket để host website
  * Tích hợp S3 với EC2 để host server
  * Kiểm tra chức năng và khả năng truy cập của website

* **Vẽ Sơ đồ Kiến trúc AWS:**
  * Học sử dụng draw.io để vẽ sơ đồ kiến trúc AWS
  * Thực hành tạo sơ đồ hạ tầng AWS chuyên nghiệp
  * Ghi chép cấu hình VPC và EC2 bằng hình ảnh

* **Tối ưu hóa Chi phí:**
  * Khám phá các chiến lược quản lý chi phí AWS
  * Học các phương pháp giảm chi phí dịch vụ AWS
  * Hiểu các công cụ thanh toán và giám sát chi phí

* **Kiểm soát Phiên bản và Công cụ AI:**
  * Khám phá các thực hành kiểm soát phiên bản Git
  * Có kinh nghiệm với khả năng và hạn chế của Kiro AI
  * Học tầm quan trọng của yêu cầu rõ ràng cho phát triển hỗ trợ bởi AI

### Thách thức gặp phải:

* **Vấn đề Triển khai Kiro AI:**
  * Gặp phải các vấn đề nghiêm trọng về code bị hỏng và hallucination khi sử dụng Kiro AI
  * Dành 2-3 ngày để debug code bị hỏng
  * Nguyên nhân gốc rễ: Yêu cầu không rõ ràng và thiếu chi tiết cho phép AI đưa ra các giả định sai
  * Bài học rút ra: Công cụ AI yêu cầu các yêu cầu chính xác, được định nghĩa rõ ràng để tạo ra code đáng tin cậy
  * Quyết định: Xóa repository bị hỏng và bắt đầu lại với cách tiếp cận rõ ràng hơn

* **Xác định Yêu cầu:**
  * Học được rằng yêu cầu chi tiết là quan trọng cho phát triển hỗ trợ bởi AI thành công
  * Hiểu khoảng cách giữa hướng dẫn chung và nhu cầu triển khai cụ thể
  * Cải thiện khả năng viết yêu cầu rõ ràng, có thể thực hiện được

### Kiến thức chính:

* VPC là nền tảng cho kiến trúc mạng và bảo mật AWS
* EC2 cung cấp khả năng tính toán linh hoạt với nhiều loại và cấu hình instance khác nhau
* S3 có thể host website tĩnh hiệu quả với cấu hình phù hợp
* Tích hợp giữa VPC, EC2 và S3 cho phép kiến trúc ứng dụng mạnh mẽ
* Tối ưu hóa chi phí là quan trọng cho việc sử dụng AWS bền vững
* Yêu cầu rõ ràng, chi tiết là cần thiết cho phát triển hỗ trợ bởi AI thành công
* Thực hành kiểm soát phiên bản giúp quản lý thay đổi code và thử nghiệm

### Mục tiêu tuần tới:

* Tiếp tục khám phá các dịch vụ AWS và tích hợp của chúng
* Áp dụng bài học về xác định yêu cầu
* Thực hành các mẫu kiến trúc AWS phức tạp hơn
* Cải thiện các chiến lược tối ưu hóa chi phí


