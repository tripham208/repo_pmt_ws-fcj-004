---
title: "Trực quan hóa dữ liệu của bạn"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 5. </b> "
---

## Sử dụng Amazon QuickSight lần đầu tiên

1. Truy cập console QuickSight, nhấp vào Đăng ký QuickSight.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-001.png?featherlight=false&width=90pc)
2. Trên trang Tạo tài khoản QuickSight của bạn, chỉ định các thông tin sau:
    * Tên tài khoản QuickSight
    * Địa chỉ email thông báo
    * Phương thức xác thực

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-002.png?featherlight=false&width=90pc)
3. Chọn vai trò IAM hiện có của bạn

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-003.png?featherlight=false&width=90pc)
4. Trên trang Tạo tài khoản QuickSight của bạn, nhấp Hoàn tất

## Kết nối với nguồn dữ liệu

1. Trên trang QuickSight, nhấp vào **Datasets** trong bảng điều hướng bên trái.
2. Ở phía trên bên phải của màn hình, nhấp **new dataset**
3. Chọn **Athena**
4. Trong cửa sổ nguồn dữ liệu Athena mới, chỉ định các thông tin sau:

    * Tên nguồn dữ liệu
    * Nhóm làm việc Athena – primary
    * Nhấp **Create Data Source**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-004.png?featherlight=false&width=90pc)

5. Trong cửa sổ Chọn bảng của bạn, chỉ định các thông tin sau:
    * Catalog – AwsDataCatalog
    * Database
    * Tables – v_yellow_tripdata

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-005.png?featherlight=false&width=90pc)

6. Trong cửa sổ hoàn tất tạo tập dữ liệu, chỉ định các thông tin sau:
7. Import to SPICE để phân tích nhanh hơn

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-006.png?featherlight=false&width=90pc)

## Trực quan hóa dữ liệu của bạn

1. QuickSight sẽ cố gắng tải dữ liệu của bạn lên SPICE, vui lòng đợi vài phút.
2. Để trực quan hóa luồng chuyến đi taxi vàng từ khu vực đón đến khu vực trả khách, nhấp vào + Thêm trong menu.
3. Chọn loại trực quan **Sankey**, chỉ định các thông tin sau trong Field wells.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-007.png?featherlight=false&width=90pc)
    * Nguồn – pu_borough
    * Điểm đến – do_borough
    * Bạn có thể nhấp vào tiêu đề loại trực quan, thay đổi nó thành Luồng Chuyến đi Taxi

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-008.png?featherlight=false&width=90pc)

## Lọc dữ liệu

1. Tạo một bộ lọc tập trung vào các chuyến đi taxi xuất phát từ Manhattan.
2. Nhập **pu_borough** và sau đó chọn nó.
3. Nhấp vào menu bên cạnh bộ lọc **pu_borough**, chọn **Chỉnh sửa**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-009.png?featherlight=false&width=90pc)
4. Bỏ chọn **Manhattan** khỏi danh sách bộ lọc, nhấp **Áp dụng**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/5/5-010.png?featherlight=false&width=90pc)
5. Thu thập thông tin chi tiết bằng cách kiểm tra luồng chuyến đi taxi dựa trên khu vực đón và khu vực trả khách.
6. Quan sát các mô hình lưu lượng giao thông.
