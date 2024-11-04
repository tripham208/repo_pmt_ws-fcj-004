---
title: "Chuẩn bị và lập danh mục dữ liệu của bạn"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## Tổng quan

Với một loạt các nguồn dữ liệu và định dạng trong data lake của bạn, điều quan trọng là phải có khả năng khám phá và lập danh mục để hiểu rõ hơn về dữ liệu bạn có và đồng thời cho phép tích hợp với các phân tích AWS được xây dựng cho mục đích cụ thể khác.

Trong bài thực hành này, chúng ta sẽ tạo AWS Glue Crawlers để tự động khám phá schema của dữ liệu được lưu trữ trong Amazon S3. Thông tin khám phá được về dữ liệu lưu trữ trong S3 sẽ được đăng ký trong AWS Glue Catalog. Điều này cho phép AWS Glue sử dụng thông tin được lưu trong catalog để xử lý ETL. Nó cũng cho phép các dịch vụ AWS khác như Amazon Athena chạy các truy vấn trên dữ liệu lưu trữ trong Amazon S3.

![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2-001.png?featherlight=false&width=90pc)
