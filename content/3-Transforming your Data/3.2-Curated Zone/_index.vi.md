---
title: "Chuyển đổi sang Curated Zone"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 3.2 </b> "
---

## Lập kế hoạch các bước chuyển đổi dữ liệu

Thực hành tốt là lập kế hoạch các bước chuyển đổi dữ liệu của bạn. Dựa trên thông tin đã thu thập được trong giai đoạn
khám phá dữ liệu, chúng ta có thể đưa ra các bước chuyển đổi sau:

1. Đọc dữ liệu chuẩn hóa từ S3.
2. Thực hiện chuyển đổi dữ liệu: Kết hợp bảng yellow_tripdata với taxi_zone_lookup để lấy vị trí đón, vị trí trả khách.
3. Lưu tập dữ liệu đã xử lý vào S3 ở định dạng tối ưu hóa truy vấn.
4. Truy vấn dữ liệu đã chuyển đổi trong Athena.

## Tạo Glue job từ Standardize đến Curated

1. Truy cập Glue console.
2. Trong thanh điều hướng bên trái, nhấp vào **ETL jobs**.
3. Trên trang AWS Glue Studio, nhấp vào **Visual ETL**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-001.png?featherlight=false&width=90pc)

4. Thêm taxi_zone_lookup đón từ Glue Data Catalog
    * Nhấp vào biểu tượng Nguồn, chọn **Glue Data Catalog**.
    * Chọn **Cơ sở dữ liệu Chuẩn hóa** của bạn và bảng **taxi_zone_lookup**
    * Đổi tên nút với hậu tố **đón**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-001.png?featherlight=false&width=90pc)

5. Thêm yellow_tripdata từ Glue Data Catalog
    * Nhấp vào biểu tượng Nguồn, chọn **Glue Data Catalog**.
    * Chọn **Cơ sở dữ liệu Chuẩn hóa** của bạn và bảng **yellow_tripdata**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-002.png?featherlight=false&width=90pc)

6. Sửa đổi tên cột của taxi_zone_lookup đón
    * Chọn nút taxi_zone_lookup đón
    * Nhấp vào biểu tượng **Chuyển đổi**, chọn **Thay đổi Lược đồ**.
    * Đổi tên cột với tiền tố **pu**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-003.png?featherlight=false&width=90pc)

7. Kết hợp yellow_tripdata với taxi_zone_lookup đón đã chuyển đổi
    * Chọn nút yellow_tripdata
    * Nhấp vào biểu tượng **Chuyển đổi**, chọn **Kết hợp**.
    * Cập nhật nút cha
    * Đổi tên nút với hậu tố **đón**
    * Trong điều kiện Kết hợp, chọn các khóa sau:
        * **taxi_zone_lookup đón** - pu_location_id
        * **yellow_tripdata** - pulocationid

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-004.png?featherlight=false&width=90pc)

8. Thêm taxi_zone_lookup trả khách từ Glue Data Catalog
    * Nhấp vào biểu tượng Nguồn, chọn **Glue Data Catalog**.
    * Chọn **Cơ sở dữ liệu Chuẩn hóa** của bạn và bảng **taxi_zone_lookup**
    * Đổi tên nút với hậu tố **trả khách**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-005.png?featherlight=false&width=90pc)

9. Sửa đổi tên cột của taxi_zone_lookup trả khách
    * Chọn nút taxi_zone_lookup trả khách
    * Nhấp vào biểu tượng **Chuyển đổi**, chọn **Thay đổi Lược đồ**.
    * Đổi tên cột với tiền tố **do**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-006.png?featherlight=false&width=90pc)

10. Kết hợp taxi_zone_lookup trả khách đã chuyển đổi
    * Chọn nút **kết hợp đón**
    * Nhấp vào biểu tượng **Chuyển đổi**, chọn **Kết hợp**.
    * Cập nhật nút cha
    * Trong điều kiện Kết hợp, chọn các khóa sau:
        * **taxi_zone_lookup trả khách** - do_location_id
        * **yellow_tripdata** - dolocationid

    ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-007.png?featherlight=false&width=90pc)

11. Lưu dữ liệu đã chuyển đổi vào Amazon S3
    * Nhấp vào biểu tượng Mục tiêu, chọn Amazon S3.
    * Chỉ định các thông tin sau
        * **Định dạng** – Iceberg
        * **Loại Nén** - GZIP
        * Địa điểm Mục tiêu S3 `S3://{Curated_BUCKET}/`
        * Chọn **Cơ sở dữ liệu Đã Chọn** của bạn và nhập bảng **yellow_tripdata**

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-008.png?featherlight=false&width=90pc)
    * Xem lại sơ đồ

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-009.png?featherlight=false&width=90pc)

12. Đặt chi tiết công việc
    * Chỉ định vai trò Iam

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/1/31-005.png?featherlight=false&width=90pc)

13. Chạy công việc
    * Nhấp **Chạy**.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-010.png?featherlight=false&width=90pc)
    * Kiểm tra nhật ký.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-011.png?featherlight=false&width=90pc)

    * Kiểm tra số liệu

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-012.png?featherlight=false&width=90pc)

14. Kiểm tra đầu ra
    * Truy cập **bucket chuẩn hóa** trong S3 console.

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-013.png?featherlight=false&width=90pc)

### Truy vấn dữ liệu Đã Chọn

1. Chọn **Curated**
2. Chọn **yellow_tripdata**
3. Chọn **xem trước bảng**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-016.png?featherlight=false&width=90pc)
4. Xem lại schema
    * Chọn **yellow_tripdata**
    * Nhấp **View in glue**

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-014.png?featherlight=false&width=90pc)

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/3/2/32-015.png?featherlight=false&width=90pc)
