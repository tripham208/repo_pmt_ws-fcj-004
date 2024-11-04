---
title: "Chuyển đổi dữ liệu tới Standardize Zone"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

## Lập kế hoạch các bước chuyển đổi dữ liệu

Đây là một thực hành tốt để lập kế hoạch các bước chuyển đổi dữ liệu của bạn. Dựa trên thông tin mà chúng ta thu thập
được trong giai đoạn khám phá dữ liệu, chúng ta có thể đưa ra các bước chuyển đổi sau:

1. Đọc dữ liệu thô từ S3.
2. Thực hiện chuyển đổi dữ liệu: Đặt các loại dữ liệu phù hợp.
3. Lưu tập dữ liệu đã xử lý vào S3 trong định dạng tối ưu hóa truy vấn.
4. Chạy các crawler để tạo bảng.
5. Truy vấn dữ liệu đã chuyển đổi trong Athena.

## Tạo Glue job chuyển đổi dữ liệu từ Raw đến Standardize

1. Truy cập Glue console.
2. Trong bảng điều hướng bên trái, nhấn vào **ETL jobs**.
3. Trên trang AWS Glue Studio, nhấn vào **Visual ETL**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-001.png?featherlight=false&width=90pc)

### taxi_zone_lookup

1. Thêm dữ liệu Yellow Trips từ Amazon S3
    * Nhấn vào biểu tượng Source, chọn **S3**.
    * Trong **Data source – S3 bucket node**, chỉ định thông tin sau:
        * S3 URL: `S3://{RAW_BUCKET}/nyc-taxi/taxi_zone_lookup/`

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-002.png?featherlight=false&width=90pc)

2. Thay đổi loại dữ liệu
    * Nhấn vào biểu tượng **Transform**, chọn **Change Schema**.
    * Thay đổi loại dữ liệu

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-003.png?featherlight=false&width=90pc)

3. Lưu dữ liệu đã chuyển đổi vào Amazon S3
    * Nhấn vào biểu tượng Target, chọn Amazon S3.
    * Chỉ định thông tin sau
        * **Format** – Parquet
        * **Compression Type** - Snappy
        * Vị trí S3 Target `S3://{Standardize_BUCKET}/taxi_zone_lookup/`

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-004.png?featherlight=false&width=90pc)

4. Đặt chi tiết công việc
    * Chỉ định IAM role

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-005.png?featherlight=false&width=90pc)

5. Chạy công việc
    * Nhấn **Run**.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-006.png?featherlight=false&width=90pc)

6. Kiểm tra đầu ra
    * Truy cập **standardize bucket** trong S3 console.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-007.png?featherlight=false&width=90pc)

### yellow_tripdata

1. Thêm dữ liệu Yellow Trips từ Amazon S3
    * Nhấn vào biểu tượng Source, chọn **S3**.
    * Trong **Data source – S3 bucket node**, chỉ định thông tin sau:
        * S3 URL: `S3://{RAW_BUCKET}/nyc-taxi/yellow_tripdata/`

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-008.png?featherlight=false&width=90pc)

2. Thay đổi loại dữ liệu
    * Nhấn vào biểu tượng **Transform**, chọn **Change Schema**.
    * Thay đổi loại dữ liệu

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-009.png?featherlight=false&width=90pc)

3. Lưu dữ liệu đã chuyển đổi vào Amazon S3
    * Nhấn vào biểu tượng Target, chọn Amazon S3.
    * Chỉ định thông tin sau
        * **Format** – Parquet
        * **Compression Type** - Snappy
        * Vị trí S3 Target `S3://{Standardize_BUCKET}/yellow_tripdata/`

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-010.png?featherlight=false&width=90pc)

4. Đặt chi tiết công việc
    * Chỉ định IAM role

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-005.png?featherlight=false&width=90pc)

5. Chạy công việc
    * Nhấn **Run**.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-011.png?featherlight=false&width=90pc)

6. Kiểm tra đầu ra
    * Truy cập **standardize bucket** trong S3 console.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-012.png?featherlight=false&width=90pc)

## Chạy Crawlers để tạo bảng

1. Truy cập AWS Glue Console.
2. Trong menu điều hướng bên trái, nhấn vào **Crawlers**.
3. Trên trang Crawlers, chọn crawler của bạn, sau đó nhấn **Run crawler**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-013.png?featherlight=false&width=90pc)
4. Trong menu điều hướng bên trái, nhấn vào **Tables**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-014.png?featherlight=false&width=90pc)
5. Trên trang Tables, nhấn vào **tên bảng** để xem thông tin siêu dữ liệu và schema của bảng.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-015.png?featherlight=false)

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-016.png?featherlight=false)

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-017.png?featherlight=false)

## Truy vấn dữ liệu đã chuyển đổi trong Athena

### Sử dụng Amazon Athena lần đầu tiên

Amazon Athena tự động lưu trữ kết quả truy vấn và thông tin siêu dữ liệu cho mỗi truy vấn chạy trong một vị trí kết quả
truy vấn mà bạn có thể chỉ định trong Amazon S3. Nếu cần, bạn có thể truy cập các tệp trong vị trí này để làm việc với
chúng. Bạn cũng có thể tải xuống các tệp kết quả truy vấn trực tiếp từ bảng điều khiển Athena.

1. Truy cập Athena console. Nhấn **Get Started**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-018.png?featherlight=false&width=90pc)
2. Chọn **Edit Settings**, nhấn vào **Browse S3** và chọn bucket làm giá trị cho trường Location of query result -
   optional.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-019.png?featherlight=false&width=90pc)

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-020.png?featherlight=false&width=90pc)
3. Truy cập menu trên cùng, nhấn vào **Editor** để quay lại trang Query editor.

### Truy vấn dữ liệu Standardize

1. Chọn **database**
2. Chọn **table**
3. Chọn **preview table**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-021.png?featherlight=false&width=90pc)

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-022.png?featherlight=false&width=90pc)