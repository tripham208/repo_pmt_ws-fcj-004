---
title: "Tạo Crawler"
date: "`r Sys.Date()`"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

Glue Crawler là một tính năng tự động suy luận cơ sở dữ liệu và schema bảng từ dữ liệu nguồn của bạn, sau đó lưu trữ siêu dữ liệu liên quan trong AWS Glue Data Catalog.

## Tạo Crawler cho bảng **taxi_zone_lookup**

1. Truy cập AWS Glue Console.
2. Trong menu điều hướng bên trái, nhấn vào **Crawlers**.
3. Trên trang Crawlers, nhấn vào **Create a crawler**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/4/24-001.png?featherlight=false&width=90pc)

4. Chỉ định tên cho crawler, nhấn **Next**.
5. Trên màn hình Choose data sources and classifiers, chỉ định thông tin sau, sau đó nhấn **Next**.

    * Nhấn Add a data source
    * Chọn một Data source – **S3**
    * Chọn Location of S3 data - **In this account**
    * Bao gồm S3 path – s3://{Standardize_BUCKET}/taxi_zone_lookup/
    * Đối với các lần chạy crawler sau, chọn Crawl all sub-folders
    * Sau đó nhấn Add an S3 data source.

6. Trên Configure security settings, chọn datalake role của bạn từ Existing IAM role, nhấn **Next**.
7. Chọn cơ sở dữ liệu **Standardize** của bạn.
8. Trên Crawler schedule, để tần suất **On demand**, nhấn **Next**.
9. Xem lại chi tiết crawler, nhấn **Create crawler**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/4/24-002.png?featherlight=false&width=90pc)

## Tạo Crawler cho bảng **yellow_tripdata**

1. Truy cập AWS Glue Console.
2. Trong menu điều hướng bên trái, nhấn vào **Crawlers**.
3. Trên trang Crawlers, nhấn vào **Create a crawler**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/4/24-001.png?featherlight=false&width=90pc)

4. Chỉ định tên cho crawler, nhấn **Next**.
5. Trên màn hình Choose data sources and classifiers, chỉ định thông tin sau, sau đó nhấn **Next**.

    * Nhấn **Add a data source**
    * Chọn một Data source – **S3**
    * Chọn Location of S3 data - **In this account**
    * Bao gồm S3 path – s3://{Standardize_BUCKET}/yellow_tripdata/
    * Đối với các lần chạy crawler sau, chọn Crawl all sub-folders
    * Sau đó nhấn Add an S3 data source.

6. Trên Configure security settings, chọn datalake role của bạn từ Existing IAM role, nhấn **Next**.
7. Chọn cơ sở dữ liệu **Standardize** của bạn.
8. Trên Crawler schedule, để tần suất **On demand**, nhấn **Next**.
9. Xem lại chi tiết crawler, nhấn **Create crawler**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/4/24-003.png?featherlight=false&width=90pc)
