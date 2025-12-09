## [**Trí tuệ nhân tạo**](https://aws.amazon.com/blogs/machine-learning/)

# **Xây dựng các ứng dụng RAG hiệu quả về chi phí với Knowledge Bases của Amazon Bedrock và Amazon S3 Vectors**

bởi **Vaibhav Sabharwal**, **Ashish Lal**, **Dani Mitchell**, và **Irene Marban**  
vào ngày 17 THÁNG 7 NĂM 2025  
trong [**Amazon Bedrock**](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/), [**Amazon Bedrock Knowledge Bases**](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/amazon-bedrock-knowledge-bases/), [**Amazon Machine Learning**](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/amazon-machine-learning/), [**Trí tuệ nhân tạo**](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/)

Nhúng véc-tơ (vector embeddings) đã trở nên thiết yếu cho các ứng dụng [Sinh dữ liệu tăng cường truy xuất (RAG)](https://aws.amazon.com/what-is/retrieval-augmented-generation/) hiện đại, nhưng các tổ chức phải đối mặt với những thách thức đáng kể về chi phí khi mở rộng quy mô. Khi các cơ sở tri thức phát triển và yêu cầu các nhúng chi tiết hơn, nhiều cơ sở dữ liệu véc-tơ dựa trên lưu trữ hiệu suất cao như SSD hoặc giải pháp trong bộ nhớ trở nên đắt đỏ đến mức không thể chi trả. Rào cản chi phí này thường buộc các tổ chức phải giới hạn phạm vi của các ứng dụng RAG của họ hoặc thỏa hiệp về mức độ chi tiết của các biểu diễn véc-tơ, có khả năng ảnh hưởng đến chất lượng kết quả. Ngoài ra, đối với các trường hợp sử dụng liên quan đến dữ liệu lịch sử hoặc lưu trữ vẫn cần có thể tìm kiếm được, việc lưu trữ véc-tơ trong các cơ sở dữ liệu véc-tơ chuyên dụng được tối ưu hóa cho khối lượng công việc thông lượng cao là một khoản chi phí liên tục không cần thiết.

Bắt đầu từ ngày 15 tháng 7, khách hàng của [Amazon Bedrock Knowledge Bases](https://aws.amazon.com/bedrock/knowledge-bases/) có thể chọn [Amazon S3 Vectors](https://aws.amazon.com/s3/features/vectors/) (bản xem trước), dịch vụ lưu trữ đối tượng đám mây đầu tiên có hỗ trợ tích hợp để lưu trữ và truy vấn véc-tơ với chi phí thấp, làm kho lưu trữ véc-tơ. Người dùng Amazon Bedrock Knowledge Bases giờ đây có thể giảm chi phí tải lên, lưu trữ và truy vấn véc-tơ lên đến 90%. Được thiết kế để lưu trữ bền vững và tối ưu hóa chi phí cho các bộ dữ liệu véc-tơ lớn với hiệu suất truy vấn dưới một giây, S3 Vectors là lựa chọn lý tưởng cho các ứng dụng RAG yêu cầu lưu trữ dài hạn khối lượng véc-tơ khổng lồ và có thể chấp nhận sự đánh đổi về hiệu suất so với các cơ sở dữ liệu véc-tơ có số truy vấn mỗi giây (QPS) cao và độ trễ mili giây. Việc tích hợp với [Amazon Bedrock](https://aws.amazon.com/bedrock/) có nghĩa là bạn có thể xây dựng các ứng dụng RAG tiết kiệm hơn trong khi vẫn duy trì hiệu suất tìm kiếm ngữ nghĩa cần thiết cho kết quả chất lượng.

Trong bài đăng này, chúng tôi trình bày cách tích hợp Amazon S3 Vectors với Amazon Bedrock Knowledge Bases cho các ứng dụng RAG. Bạn sẽ học được một phương pháp thực tế để mở rộng quy mô cơ sở tri thức của mình để xử lý hàng triệu tài liệu trong khi vẫn duy trì chất lượng truy xuất và sử dụng bộ lưu trữ hiệu quả về chi phí của S3 Vectors.

## **Tổng quan về tích hợp Amazon Bedrock Knowledge Bases và Amazon S3 Vectors**

Khi tạo một knowledge base trong Amazon Bedrock, bạn có thể chọn S3 Vectors làm tùy chọn lưu trữ véc-tơ của mình. Sử dụng phương pháp này, bạn có thể xây dựng các ứng dụng RAG có thể mở rộng, hiệu quả về chi phí mà không cần cấp phép hoặc quản lý cơ sở hạ tầng phức tạp. Việc tích hợp mang lại sự tiết kiệm chi phí đáng kể trong khi vẫn duy trì hiệu suất truy vấn dưới một giây, làm cho nó trở nên lý tưởng để làm việc với các bộ dữ liệu véc-tơ lớn hơn được tạo ra từ khối lượng lớn dữ liệu phi cấu trúc bao gồm văn bản, hình ảnh, âm thanh và video. Sử dụng mô hình định giá trả theo mức sử dụng với các mức giá thấp, S3 Vectors cung cấp khả năng tối ưu hóa chi phí hàng đầu trong ngành, giúp giảm chi phí tải lên, lưu trữ và truy vấn véc-tơ lên đến 90% so với các giải pháp thay thế. Các khả năng tìm kiếm nâng cao bao gồm lọc siêu dữ liệu phong phú, vì vậy bạn có thể tinh chỉnh các truy vấn theo thuộc tính tài liệu như ngày tháng, danh mục và nguồn. Sự kết hợp giữa S3 Vectors và Amazon Bedrock là lý tưởng cho các tổ chức xây dựng các cơ sở tri thức quy mô lớn đòi hỏi cả hiệu quả chi phí và khả năng truy xuất hiệu quả—từ việc quản lý các kho tài liệu mở rộng đến các kho lưu trữ lịch sử và các ứng dụng yêu cầu biểu diễn véc-tơ chi tiết. Hướng dẫn này bao gồm các bước cấp cao sau:

1. Tạo một knowledge base mới  
2. Cấu hình nguồn dữ liệu  
3. Cấu hình nguồn dữ liệu và xử lý  
4. Đồng bộ hóa nguồn dữ liệu  
5. Kiểm tra knowledge base

## **Điều kiện tiên quyết**

Trước khi bắt đầu, hãy đảm bảo rằng bạn có các điều kiện tiên quyết sau:

* Một tài khoản AWS có quyền truy cập dịch vụ phù hợp.  
* Một vai trò [AWS Identity and Access Management](https://aws.amazon.com/iam/) (IAM) với các quyền phù hợp để truy cập Amazon Bedrock và [Amazon Simple Storage Service](https://aws.amazon.com/s3/) (Amazon S3).  
* Bật [quyền truy cập mô hình](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html) cho các mô hình nhúng và suy luận như [Amazon Titan Text Embeddings V2](https://aws.amazon.com/bedrock/amazon-models/titan/) và [Amazon Nova Pro](https://aws.amazon.com/ai/generative-ai/nova/).

## **Hướng dẫn tích hợp Amazon Bedrock Knowledge Bases và Amazon S3 Vectors**

Trong phần này, chúng tôi sẽ hướng dẫn quy trình từng bước để tạo một knowledge base với Amazon S3 Vectors bằng cách sử dụng [Bảng điều khiển quản lý AWS](https://aws.amazon.com/console/). Chúng tôi sẽ bao quát toàn bộ quy trình từ việc cấu hình kho lưu trữ véc-tơ đến việc nhập tài liệu và kiểm tra khả năng truy xuất của bạn.

Đối với những người thích cấu hình knowledge base của họ theo chương trình thay vì sử dụng bảng điều khiển, kho lưu trữ [Amazon Bedrock Knowledge Bases with S3 Vectors](https://github.com/aws-samples/amazon-bedrock-samples/blob/main/rag/knowledge-bases/features-examples/10-s3-vectors/knowledge-base-s3-vector.ipynb) trên GitHub cung cấp một sổ tay hướng dẫn mà bạn có thể làm theo để triển khai thiết lập trong tài khoản của riêng mình.

### **Tạo một knowledge base mới**

Để tạo một knowledge base mới, hãy làm theo các bước sau:

1. Trên bảng điều khiển Amazon Bedrock trong ngăn điều hướng bên trái, chọn **Knowledge Bases**. Để bắt đầu quá trình tạo, trong danh sách thả xuống **Create**, chọn **Knowledge Base with vector store**.  
2. Trên trang **Provide Knowledge Base details**, nhập tên mô tả cho knowledge base của bạn và một mô tả tùy chọn để xác định mục đích của nó. Chọn phương pháp cấp quyền IAM của bạn—tạo một vai trò dịch vụ mới hoặc sử dụng một vai trò hiện có—để cấp các quyền cần thiết để truy cập các dịch vụ AWS, như được hiển thị trong ảnh chụp màn hình sau.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-1.jpeg)

1. Chọn **Amazon S3**. Tùy chọn, thêm các thẻ để giúp tổ chức và phân loại tài nguyên của bạn và cấu hình các đích đến để gửi nhật ký như một bucket S3 hoặc [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) để theo dõi và khắc phục sự cố.  
2. Chọn **Next** để tiếp tục đến phần cấu hình nguồn dữ liệu.

### **Cấu hình nguồn dữ liệu**

Để cấu hình nguồn dữ liệu, hãy làm theo các bước sau:

1. Gán một tên mô tả cho dữ liệu knowledge base của bạn.  
2. Trong **Data source location**, chọn xem bucket S3 tồn tại trong tài khoản AWS hiện tại của bạn hay một tài khoản khác, sau đó chỉ định vị trí lưu trữ tài liệu của bạn, như được hiển thị trong ảnh chụp màn hình sau.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-2.png)

Trong bước này, hãy cấu hình chiến lược phân tích cú pháp của bạn để xác định cách Amazon Bedrock xử lý tài liệu của bạn. Chọn **Amazon Bedrock default parser** cho các tài liệu chỉ có văn bản mà không mất thêm chi phí. Chọn **Amazon Bedrock Data Automation as parser or Foundation models as a parser** để xử lý các tài liệu phức tạp có các yếu tố trực quan.

Cấu hình chiến lược phân đoạn cũng quan trọng không kém vì nó xác định cách nội dung của bạn được phân đoạn thành các đơn vị có ý nghĩa để nhúng véc-tơ, ảnh hưởng trực tiếp đến chất lượng truy xuất và bảo toàn ngữ cảnh. Chúng tôi đã chọn **Fixed-size chunking** cho ví dụ này do kích thước token có thể dự đoán và sự đơn giản của nó. Vì cả quyết định phân tích cú pháp và phân đoạn đều không thể sửa đổi sau khi tạo, hãy chọn các tùy chọn phù hợp nhất với cấu trúc nội dung và nhu cầu truy xuất của bạn. Đối với dữ liệu nhạy cảm, bạn có thể sử dụng cài đặt nâng cao để triển khai mã hóa [AWS Key Management Service](https://aws.amazon.com/kms/) (AWS KMS) hoặc áp dụng các hàm chuyển đổi tùy chỉnh để tối ưu hóa tài liệu của bạn trước khi nhập. Theo mặc định, S3 Vectors sẽ sử dụng mã hóa phía máy chủ (SSE-S3).

### **Cấu hình lưu trữ và xử lý dữ liệu**

Để cấu hình lưu trữ và xử lý dữ liệu, trước tiên hãy chọn mô hình nhúng, như được hiển thị trong ảnh chụp màn hình sau. Mô hình nhúng sẽ chuyển đổi các đoạn văn bản của bạn thành các biểu diễn véc-tơ số cho khả năng tìm kiếm ngữ nghĩa. Nếu kết nối với một S3 Vector hiện có làm kho lưu trữ véc-tơ, hãy đảm bảo rằng kích thước của mô hình nhúng khớp với kích thước được sử dụng khi tạo kho lưu trữ véc-tơ của bạn vì sự không khớp về kích thước sẽ gây ra lỗi nhập. Amazon Bedrock cung cấp một số mô hình nhúng để lựa chọn, mỗi mô hình có các kích thước véc-tơ và đặc điểm hiệu suất khác nhau được tối ưu hóa cho các trường hợp sử dụng khác nhau. Hãy xem xét cả sự phong phú về ngữ nghĩa của mô hình và các tác động về chi phí của nó khi đưa ra lựa chọn của bạn.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-3.jpeg)

Tiếp theo, cấu hình kho lưu trữ véc-tơ. Đối với việc lựa chọn lưu trữ véc-tơ, hãy chọn cách Amazon Bedrock Knowledge Bases sẽ lưu trữ và quản lý các nhúng véc-tơ được tạo từ tài liệu của bạn trong Amazon S3 Vectors, bằng một trong hai tùy chọn sau:

#### ***Tùy chọn 1\. Nhanh chóng tạo một kho lưu trữ véc-tơ mới***

Tùy chọn được khuyến nghị này, được hiển thị trong ảnh chụp màn hình sau, tự động tạo một bucket S3 vector trong tài khoản của bạn trong quá trình tạo knowledge base. Hệ thống sẽ tối ưu hóa việc lưu trữ véc-tơ của bạn để lưu trữ các bộ dữ liệu véc-tơ quy mô lớn một cách bền vững và hiệu quả về chi phí, tạo ra một bucket S3 vector và một chỉ mục véc-tơ cho bạn.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-4.png)

#### ***Tùy chọn 2\. Sử dụng một kho lưu trữ véc-tơ hiện có***

Khi tạo chỉ mục Amazon S3 Vector làm kho lưu trữ véc-tơ để sử dụng với Amazon Bedrock Knowledge Bases, bạn có thể đính kèm siêu dữ liệu (chẳng hạn như năm, tác giả, thể loại và vị trí) dưới dạng các cặp khóa-giá trị cho mỗi véc-tơ. Theo mặc định, các trường siêu dữ liệu có thể được sử dụng làm bộ lọc trong các truy vấn tương tự trừ khi được chỉ định là siêu dữ liệu không thể lọc tại thời điểm tạo chỉ mục véc-tơ. Các chỉ mục S3 Vector hỗ trợ các loại chuỗi, số và Boolean lên đến 40 KB mỗi véc-tơ, với siêu dữ liệu có thể lọc được giới hạn ở mức 2 KB mỗi véc-tơ.

Để chứa các đoạn văn bản lớn hơn và siêu dữ liệu phong phú hơn trong khi vẫn cho phép lọc trên các thuộc tính quan trọng khác, hãy thêm "AMAZON\_BEDROCK\_TEXT" vào danh sách nonFilterableMetadataKeys trong cấu hình chỉ mục của bạn. Phương pháp này tối ưu hóa việc phân bổ bộ nhớ của bạn cho nội dung tài liệu trong khi vẫn duy trì khả năng lọc cho các thuộc tính có ý nghĩa như danh mục hoặc ngày tháng. Hãy nhớ rằng các trường được thêm vào mảng nonFilterableMetadataKeys không thể được sử dụng với tính năng lọc siêu dữ liệu trong các truy vấn và không thể sửa đổi sau khi chỉ mục được tạo.

Đây là một ví dụ về việc tạo một chỉ mục Amazon S3 Vector với cấu hình siêu dữ liệu phù hợp:

code CSS  
downloadcontent\_copy  
expand\_less  
   s3vectors.create\_index(  
    vectorBucketName="my-first-vector-bucket",  
    indexName="my-first-vector-index",  
    dimension=1024,  
    distanceMetric="cosine",  
    dataType="float32",    
    metadataConfiguration={"nonFilterableMetadataKeys": \["AMAZON\_BEDROCK\_TEXT"\]}   
)  
 

Để biết chi tiết về cách tạo kho lưu trữ véc-tơ, hãy tham khảo [Giới thiệu Amazon S3 Vectors](https://aws.amazon.com/blogs/aws/introducing-amazon-s3-vectors-first-cloud-storage-with-native-vector-support-at-scale/) trong Blog Tin tức của AWS.

Sau khi bạn có một bucket và chỉ mục S3 Vector, bạn có thể kết nối nó với knowledge base của mình. Bạn sẽ cần cung cấp cả [Tên tài nguyên Amazon](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference-arns.html) (ARN) của bucket S3 Vector và ARN của chỉ mục véc-tơ, như được hiển thị trong ảnh chụp màn hình sau, để liên kết chính xác knowledge base của bạn với chỉ mục S3 Vector hiện có.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-5.jpeg)

### **Đồng bộ hóa nguồn dữ liệu**

Sau khi bạn đã cấu hình knowledge base của mình với S3 Vectors, bạn cần đồng bộ hóa nguồn dữ liệu của mình để tạo và lưu trữ các nhúng véc-tơ. Từ bảng điều khiển Amazon Bedrock Knowledge Bases, hãy mở knowledge base đã tạo của bạn và tìm nguồn dữ liệu đã cấu hình của bạn và chọn **Sync** để bắt đầu quá trình, như được hiển thị trong ảnh chụp màn hình sau. Trong quá trình đồng bộ hóa, hệ thống sẽ xử lý tài liệu của bạn theo cấu hình phân tích cú pháp và phân đoạn của bạn, tạo các nhúng bằng mô hình bạn đã chọn và lưu trữ chúng trong chỉ mục S3 vector của bạn. Bạn có thể theo dõi tiến trình đồng bộ hóa trong thời gian thực nếu bạn đã cấu hình [Nhật ký Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html) và xác minh trạng thái hoàn thành trước khi kiểm tra khả năng truy xuất của knowledge base.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-6.jpeg)

### **Kiểm tra knowledge base**

Sau khi cấu hình thành công knowledge base của bạn với S3 Vectors, bạn có thể xác thực chức năng của nó bằng giao diện kiểm tra tích hợp. Bạn có thể sử dụng bảng điều khiển tương tác này để thử nghiệm với các loại truy vấn khác nhau và xem cả kết quả truy xuất và các phản hồi được tạo ra. Chọn giữa chế độ **Chỉ truy xuất** (API Retrieve) để kiểm tra các đoạn nguồn thô hoặc **Truy xuất và tạo phản hồi** (API RetrieveandGenerate) để tìm hiểu cách các [mô hình nền tảng](https://aws.amazon.com/what-is/foundation-models/) (FM) như Amazon Nova sử dụng nội dung được truy xuất của bạn. Giao diện kiểm tra cung cấp những hiểu biết có giá trị về cách knowledge base của bạn xử lý các truy vấn, hiển thị các đoạn nguồn, điểm liên quan của chúng và siêu dữ liệu liên quan.

Bạn cũng có thể cấu hình cài đặt truy vấn cho knowledge base của mình giống như với các tùy chọn lưu trữ véc-tơ khác, bao gồm các bộ lọc để lựa chọn dựa trên siêu dữ liệu, các rào cản để có phản hồi phù hợp, khả năng xếp hạng lại và các tùy chọn sửa đổi truy vấn. Những công cụ này giúp tối ưu hóa chất lượng truy xuất và đảm bảo thông tin phù hợp nhất được trình bày cho các FM của bạn. S3 Vectors hiện hỗ trợ chức năng tìm kiếm ngữ nghĩa. Sử dụng việc xác thực thực hành này, bạn có thể tinh chỉnh cấu hình của mình trước khi tích hợp knowledge base với các ứng dụng sản xuất.

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-7.jpeg)

## **Tạo knowledge base Amazon Bedrock của bạn theo chương trình**

Trong các phần trước, chúng tôi đã hướng dẫn cách tạo một knowledge base với Amazon S3 Vectors bằng Bảng điều khiển quản lý AWS. Đối với những người thích tự động hóa quy trình này hoặc tích hợp nó vào các quy trình làm việc hiện có, bạn cũng có thể tạo knowledge base của mình theo chương trình bằng cách sử dụng [AWS SDK](https://aws.amazon.com/developer/tools/).

Sau đây là một đoạn mã mẫu cho thấy lệnh gọi API trông như thế nào khi tạo một knowledge base Amazon Bedrock theo chương trình với một chỉ mục Amazon S3 Vector hiện có:

code CSS  
downloadcontent\_copy  
expand\_less  
   response \= bedrock.create\_knowledge\_base(  
    description='Amazon Bedrock Knowledge Base integrated with Amazon S3 Vectors',  
    knowledgeBaseConfiguration={  
        'type': 'VECTOR',  
        'vectorKnowledgeBaseConfiguration': {  
             'embeddingModelArn': f'arn:aws:bedrock:{region}::foundation-model/amazon.titan-embed-text-v2:0',  
             'embeddingModelConfiguration': {  
                 'bedrockEmbeddingModelConfiguration': {  
                     'dimensions': vector\_dimension, \#Verify this is the same value as S3 vector index configuration  
                     'embeddingDataType': 'FLOAT32'  
                 }  
             },  
        },  
    },  
     name=knowledge\_base\_name,  
     roleArn=roleArn,  
     storageConfiguration={  
         's3VectorsConfiguration': {  
             'indexArn': vector\_index\_arn  
         },  
         'type': 'S3\_VECTORS'  
     }  
)  
 

Vai trò được gắn với knowledge base nên có một số chính sách được đính kèm, bao gồm quyền truy cập vào API S3 Vectors, các mô hình được sử dụng để nhúng, tạo và xếp hạng lại (nếu được sử dụng), và bucket S3 được sử dụng làm nguồn dữ liệu. Nếu bạn đang sử dụng khóa do khách hàng quản lý cho S3 Vector làm kho lưu trữ véc-tơ, bạn sẽ cần cung cấp một chính sách bổ sung để cho phép giải mã dữ liệu. Sau đây là chính sách cần thiết để truy cập Amazon S3 Vector làm kho lưu trữ véc-tơ:

code Code  
downloadcontent\_copy  
expand\_less  
   {  
    "Version": "2012-10-17",  
    "Statement": \[  
        {  
            "Sid": "BedrockInvokeModelPermission",  
            "Effect": "Allow",  
            "Action": \[  
                "bedrock:InvokeModel"  
            \],  
            "Resource": \[  
                "arn:aws:bedrock:{REGION}::foundation-model/amazon.titan-embed-text-v2:0"  
            \]  
        },  
        {  
            "Sid": "KmsPermission",  
            "Effect": "Allow",  
            "Action": \[  
                "kms:GenerateDataKey",  
                "kms:Decrypt"  
            \],  
            "Resource": \[  
                "arn:aws:kms:{REGION}:{ACCOUNT\_ID}:key/{KMS\_KEY\_ID}"  
            \]  
        },  
        {  
            "Sid": "S3ListBucketPermission",  
            "Effect": "Allow",  
            "Action": \[  
                "s3:ListBucket"  
            \],  
            "Resource": \[  
                "arn:aws:s3:::{SOURCE\_BUCKET\_NAME}"  
            \],  
            "Condition": {  
                "StringEquals": {  
                    "aws:ResourceAccount": \[  
                        "{ACCOUNT\_ID}"  
                    \]  
                }  
            }  
        },  
        {  
            "Sid": "S3GetObjectPermission",  
            "Effect": "Allow",  
            "Action": \[  
                "s3:GetObject"  
            \],  
            "Resource": \[  
                "arn:aws:s3:::{SOURCE\_BUCKET\_NAME}/{PREFIX}/\*"  
            \],  
            "Condition": {  
                "StringEquals": {  
                    "aws:ResourceAccount": \[  
                        "{ACCOUNT\_ID}"  
                    \]  
                }  
            }  
        },  
        {  
            "Sid": "S3VectorsAccessPermission",  
            "Effect": "Allow",  
            "Action": \[  
                "s3vectors:GetIndex",  
                "s3vectors:QueryVectors",  
                "s3vectors:PutVectors",  
                "s3vectors:GetVectors",  
                "s3vectors:DeleteVectors"  
            \],  
            "Resource": "arn:aws:s3vectors:{REGION}:{ACCOUNT\_ID}:bucket/{VECTOR\_BUCKET\_NAME}/index/{VECTOR\_INDEX\_NAME}",  
            "Condition": {  
                "StringEquals": {  
                    "aws:ResourceAccount": "{ACCOUNT\_ID}"  
                }  
            }  
        }  
    \]  
}  
 

## **Dọn dẹp**

Để dọn dẹp tài nguyên của bạn, hãy hoàn thành các bước sau. Để xóa knowledge base:

1. Trên bảng điều khiển Amazon Bedrock, chọn **Knowledge Bases**  
2. Chọn Knowledge Base của bạn và ghi lại cả tên vai trò dịch vụ IAM và ARN chỉ mục S3 Vector  
3. Chọn **Delete** và xác nhận

Để xóa S3 Vector làm kho lưu trữ véc-tơ, hãy sử dụng các lệnh sau của [Giao diện dòng lệnh AWS](https://aws.amazon.com/cli/) (AWS CLI):

code Code  
downloadcontent\_copy  
expand\_less  
   aws s3vectors delete-index \--vector-bucket-name YOUR\_VECTOR\_BUCKET\_NAME \--index-name YOUR\_INDEX\_NAME \--region YOUR\_REGION  
aws s3vectors delete-vector-bucket \--vector-bucket-name YOUR\_VECTOR\_BUCKET\_NAME \--region YOUR\_REGION  
 

1. Trên bảng điều khiển IAM, tìm vai trò đã ghi chú trước đó  
2. Chọn và xóa vai trò

Để xóa bộ dữ liệu mẫu:

1. Trên bảng điều khiển Amazon S3, tìm bucket S3 của bạn  
2. Chọn và xóa các tệp bạn đã tải lên cho hướng dẫn này

## **Kết luận**

Sự tích hợp giữa Amazon Bedrock Knowledge Bases và Amazon S3 Vectors đại diện cho một bước tiến đáng kể trong việc làm cho các ứng dụng RAG trở nên dễ tiếp cận và khả thi về mặt kinh tế hơn ở quy mô lớn. Bằng cách sử dụng bộ lưu trữ được tối ưu hóa chi phí của Amazon S3 Vectors, các tổ chức giờ đây có thể xây dựng các cơ sở tri thức ở quy mô lớn với hiệu quả chi phí được cải thiện. Điều này có nghĩa là khách hàng có thể đạt được sự cân bằng tối ưu giữa hiệu suất và kinh tế, và bạn có thể tập trung vào việc tạo ra giá trị thông qua các ứng dụng do AI cung cấp thay vì quản lý cơ sở hạ tầng lưu trữ véc-tơ phức tạp.

Để bắt đầu với việc tích hợp Amazon Bedrock Knowledge Bases và Amazon S3 Vectors, hãy tham khảo [Sử dụng S3 Vectors với Amazon Bedrock Knowledge Bases](https://docs.aws.amazon.com/AmazonS3/latest/userguide/s3-vectors-bedrock-kb.html) trong Hướng dẫn sử dụng Amazon S3.

---

### **Về các tác giả**

\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-8.jpeg)

**Vaibhav Sabharwal** là một Kiến trúc sư Giải pháp Cấp cao của Amazon Web Services (AWS) có trụ sở tại New York. Anh đam mê học hỏi các công nghệ đám mây mới và hỗ trợ khách hàng xây dựng chiến lược áp dụng đám mây, thiết kế các giải pháp sáng tạo và thúc đẩy sự xuất sắc trong vận hành. Là một thành viên của Cộng đồng Kỹ thuật Dịch vụ Tài chính tại AWS, anh tích cực đóng góp vào các nỗ lực hợp tác trong ngành.  
\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2024/12/09/ML-17210-dani.jpg)

**Dani Mitchell** là một Kiến trúc sư Giải pháp Chuyên gia về AI Tạo sinh tại Amazon Web Services (AWS). Anh tập trung vào việc giúp các doanh nghiệp trên toàn thế giới đẩy nhanh hành trình AI tạo sinh của họ với Amazon Bedrock.  
\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/17/ml-19266-image-10-1.png)

**Irene Marban** là một Kiến trúc sư Giải pháp Chuyên gia về AI Tạo sinh tại Amazon Web Services (AWS), làm việc với các khách hàng trên khắp EMEA để thiết kế và triển khai các giải pháp AI tạo sinh nhằm thúc đẩy hoạt động kinh doanh của họ. Với nền tảng về kỹ thuật y sinh và AI, công việc của cô tập trung vào việc giúp các tổ chức tận dụng các công nghệ AI mới nhất để thúc đẩy sự đổi mới và tăng trưởng. Khi rảnh rỗi, cô thích đọc sách và nấu ăn cho bạn bè.  
\!\[alt text\](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2023/11/22/Ashish.jpg)

**Ashish Lal** là Giám đốc Tiếp thị Sản phẩm Cấp cao về AI/ML cho Amazon Bedrock. Anh có hơn 11 năm kinh nghiệm trong lĩnh vực tiếp thị sản phẩm và thích giúp khách hàng đẩy nhanh thời gian tạo ra giá trị và giảm chi phí vòng đời AI của họ.  
