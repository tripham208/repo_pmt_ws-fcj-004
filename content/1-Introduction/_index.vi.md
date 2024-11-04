---
title: "Giới thiệu"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

## Data lake là gì?

Data lake là một kho lưu trữ tập trung cho phép bạn lưu trữ tất cả dữ liệu có cấu trúc và phi cấu trúc ở bất kỳ quy mô
nào. Bạn có thể lưu trữ dữ liệu của mình nguyên bản mà không cần phải cấu trúc dữ liệu trước và chạy các loại phân tích
khác nhau — từ bảng điều khiển và trực quan hóa đến xử lý dữ liệu lớn, phân tích thời gian thực và học máy để đưa ra
quyết định tốt hơn.

## Tổng quan về Workshop

Trong Workshop này, chúng ta sẽ lưu trữ dữ liệu trong S3 và sử dụng Glue để chuyển đổi dữ liệu. Sau đó sử dụng Athena để
phân tích và trực quan hóa trong Quicksight. Chúng ta sẽ sử dụng tập dữ liệu về **NYC Yellow Trips**

* Tải dữ liệu thô (CSV) lên khu vực Raw trong [Amazon S3](https://aws.amazon.com/vi/s3)
* Sử dụng [AWS Glue](https://aws.amazon.com/vi/glue/) để chuyển đổi dữ liệu từ khu vực Raw sang khu vực Standardize và
  lưu nó dưới định dạng [Parquet](https://parquet.apache.org/). Dữ liệu ở định dạng này, chúng ta sẽ cần tạo Crawler để
  tạo bảng và đọc dữ liệu trong Glue Catalog, Athena
* Sử dụng [AWS Glue](https://aws.amazon.com/vi/glue/) để chuyển đổi dữ liệu từ khu vực Standardize sang khu vực Curated
  với các phép chuyển đổi phức tạp hơn và lưu nó dưới định dạng [Iceberg](https://iceberg.apache.org/)
* Để phân tích dữ liệu đã chuyển đổi, chúng ta sẽ sử dụng [Amazon Athena](https://aws.amazon.com/vi/athena/)
* Để trực quan hóa dữ liệu đã phân tích, chúng ta sẽ sử dụng [Amazon QuickSight](https://aws.amazon.com/vi/quicksight/)

![Hình ảnh](/repo_pmt_ws-fcj-004/images/001.png?featherlight=false&width=90pc)

## Giới thiệu về Amazon S3

Amazon Simple Storage Service (S3) là dịch vụ lưu trữ đối tượng lớn nhất và có hiệu suất cao nhất cho dữ liệu có cấu
trúc và phi cấu trúc và là dịch vụ lưu trữ được lựa chọn để xây dựng data lake. Với Amazon S3, bạn có thể xây dựng và mở
rộng data lake với bất kỳ kích thước nào một cách hiệu quả và an toàn, nơi dữ liệu được bảo vệ bởi 99,999999999% (11 số
9) độ bền.

Với các data lake được xây dựng trên Amazon S3, bạn có thể sử dụng các dịch vụ gốc của AWS để chạy phân tích dữ liệu
lớn, trí tuệ nhân tạo (AI) và học máy (ML) để thu thập thông tin chi tiết từ các tập dữ liệu phi cấu trúc của bạn. Dữ
liệu có thể được thu thập từ nhiều nguồn và chuyển vào data lake ở định dạng ban đầu. Nó có thể được truy cập hoặc xử lý
bằng các công cụ và khung phân tích của AWS được xây dựng cho mục đích cụ thể mà bạn chọn. Điều này giúp dễ dàng và
nhanh chóng chạy phân tích mà không cần phải di chuyển dữ liệu của bạn sang hệ thống phân tích riêng biệt.

## Giới thiệu về AWS Glue

AWS Glue là một dịch vụ ETL (trích xuất, chuyển đổi và tải) serverless hoàn toàn được quản lý giúp bạn đơn giản hóa và
tiết kiệm chi phí trong việc phân loại dữ liệu, làm sạch, làm phong phú và di chuyển dữ liệu một cách tin cậy giữa các
kho dữ liệu khác nhau. AWS Glue bao gồm các thành phần cốt lõi sau:

* Data Catalog – một kho trung tâm để lưu trữ siêu dữ liệu cấu trúc và vận hành của các tài sản dữ liệu của bạn.
* ETL Engine – tự động tạo mã Scala hoặc Python.
* Jobs System – cung cấp cơ sở hạ tầng được quản lý để điều phối quy trình ETL của bạn.

AWS Glue cũng bao gồm các thành phần bổ sung như:

* [AWS Glue DataBrew](https://aws.amazon.com/glue/features/databrew/) - Một công cụ chuẩn bị dữ liệu trực quan giúp các
  nhà phân tích dữ liệu và nhà khoa học dữ liệu dễ dàng chuẩn bị dữ liệu với giao diện trực quan tương tác mà không cần
  viết mã.
* [AWS Glue Elastic Views](https://aws.amazon.com/glue/) - Xây dựng các chế độ xem vật chất hóa kết hợp và sao chép dữ
  liệu giữa nhiều kho dữ liệu mà không cần bạn phải viết mã tùy chỉnh.
* AWS Glue Studio là một giao diện đồ họa giúp bạn dễ dàng tạo, chạy và giám sát các công việc ETL trong AWS Glue. Bạn
  có thể tạo các quy trình chuyển đổi dữ liệu một cách trực quan, AWS Glue Studio sẽ tạo mã Apache Spark thay cho bạn và
  để nó chạy một cách liền mạch trên engine ETL serverless dựa trên Apache Spark của AWS Glue.

Cùng nhau, những thành phần này tự động hóa nhiều công việc nặng nề không khác biệt liên quan đến việc khám phá, phân
loại, làm sạch, làm phong phú và di chuyển dữ liệu, để bạn có thể dành nhiều thời gian hơn để phân tích dữ liệu của
mình.

## Giới thiệu về Amazon Athena

Amazon Athena là một dịch vụ truy vấn tương tác giúp dễ dàng phân tích dữ liệu trong Amazon S3 bằng cách sử dụng SQL
chuẩn. Athena là dịch vụ serverless, vì vậy không có cơ sở hạ tầng nào cần quản lý và bạn chỉ phải trả tiền cho các truy
vấn mà bạn chạy. Athena dễ sử dụng. Chỉ cần trỏ đến dữ liệu của bạn trong Amazon S3, định nghĩa schema và bắt đầu truy
vấn bằng SQL chuẩn. Hầu hết các kết quả được trả về trong vài giây. Với Athena, không cần các job ETL phức tạp để chuẩn
bị dữ liệu của bạn cho phân tích. Điều này giúp dễ dàng cho bất kỳ ai có kỹ năng SQL nhanh chóng phân tích các tập dữ
liệu lớn. Athena được tích hợp sẵn với AWS Glue Data Catalog, cho phép bạn tạo một kho siêu dữ liệu hợp nhất trên nhiều
dịch vụ khác nhau, thu thập dữ liệu để khám phá schema và điền vào Catalog của bạn với các bảng và định nghĩa phân vùng
mới và đã sửa đổi, và duy trì phiên bản schema.

## Giới thiệu về Amazon QuickSight

Amazon QuickSight là một dịch vụ BI (business intelligence) có khả năng mở rộng, không cần server, có tích hợp học máy (
ML) được xây dựng cho đám mây. Nó cho phép bạn tạo và xuất bản các bảng điều khiển tương tác và các báo cáo có định dạng
cao có thể truy cập thông qua trình duyệt web hoặc thiết bị di động.
