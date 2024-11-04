---
title: "Chuẩn bị dữ liệu của bạn"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---


## Tải lên dữ liệu thô
Chúng ta sẽ tải dữ liệu ở định dạng CSV lên S3 Raw bucket
* taxi_zone_lookup: dữ liệu về địa điểm của các chuyến đi
* yellow_tripdata: dữ liệu thông tin chuyến xe

1. Truy cập **S3 Raw bucket** trong AWS Console.
2. Tạo thư mục **taxi_zone_lookup** và **yellow_tripdata**

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/3/23-001.png?featherlight=false&width=90pc)

3. Tải xuống các tệp này: [taxi_zone_lookup](/repo_pmt_ws-fcj-004/resources/taxi_zone_lookup.csv), [yellow_tripdata](/repo_pmt_ws-fcj-004/resources/yellow_tripdata_2020-04.csv)
4. Tải lên tệp [taxi_zone_lookup](/repo_pmt_ws-fcj-004/resources/taxi_zone_lookup.csv) vào thư mục **taxi_zone_lookup**
5. Tải lên tệp [yellow_tripdata](/repo_pmt_ws-fcj-004/resources/yellow_tripdata_2020-04.csv) vào thư mục **yellow_tripdata**
