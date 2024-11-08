---
title: "Truy vấn dữ liệu của bạn"
date: "`r Sys.Date()`"
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

## Xác thực dữ liệu đã chuyển đổi

1. Truy cập console Athena.
2. Trên trang Trình soạn thảo truy vấn, chạy các truy vấn sau để kiểm tra dữ liệu.
   ```sql
   SELECT DATE_TRUNC('month', pickup_datetime) "Period", 
       COUNT(*) "Total Records"
   FROM   yellow_tripdata
   GROUP BY DATE_TRUNC('month', pickup_datetime)
   ORDER BY 1;
   ```
   ```sql
   SELECT COUNT(*) "Count"
   FROM   yellow_tripdata;
   ```
## Làm giàu dữ liệu đã chuyển đổi

1. Chạy truy vấn sau để tạo một view nhằm làm giàu bảng với dữ liệu bổ sung.

   ```sql
   CREATE OR REPLACE VIEW v_yellow_tripdata
   AS
   SELECT CASE vendor_id
               WHEN 1 THEN 'Creative Mobile'
               WHEN 2 THEN 'VeriFone'
               ELSE 'No Data'
          END "vendor_name",
          pickup_datetime,
          dropoff_datetime,
          passenger_count,
          trip_distance,
          CASE ratecodeid
               WHEN 1 THEN 'Standard Rate'
               WHEN 2 THEN 'JFK'
               WHEN 3 THEN 'Newark'
               WHEN 4 THEN 'Nassau/Westchester'
               WHEN 5 THEN 'Negotiated Fare'
               WHEN 6 THEN 'Group Ride'
               WHEN 99 THEN 'Special Rate'
               ELSE 'No Data'
          END "rate_type",
          store_and_fwd_flag,
          pu_borough,
          pu_zone,
          pu_service_zone,
          do_borough,
          do_zone,
          do_service_zone,
          CASE payment_type
               WHEN 1 THEN 'Credit Card'
               WHEN 2 THEN 'Cash'
               WHEN 3 THEN 'No Charge'
               WHEN 4 THEN 'Dispute'
               WHEN 5 THEN 'Unknown'
               WHEN 6 THEN 'Voided Trip'
               ELSE 'No Data'
          END "payment_type",
          fare_amount,
          extra,
          mta_tax,
          tip_amount,
          tolls_amount,
          improvement_surcharge,
          congestion_surcharge,
          total_amount
   FROM   yellow_tripdata;
   ```


2. Chọn Xem trước bảng để kiểm tra dữ liệu đã làm giàu trong view v_yellow_tripdata.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/4/4-001.png?featherlight=false&width=90pc)
3. Chạy truy vấn sau để lấy thông tin chi tiết.
   ```sql
   SELECT vendor_name "Vendor",
          rate_type "Rate Type", 
          payment_type "Payment Type",
          ROUND(AVG(fare_amount), 2) "Fare",
          ROUND(AVG(extra), 2) "Extra",
          ROUND(AVG(mta_tax), 2) "MTA",
          ROUND(AVG(tip_amount), 2) "Tip",
          ROUND(AVG(tolls_amount), 2) "Toll",
          ROUND(AVG(improvement_surcharge), 2) "Improvement",
          ROUND(AVG(congestion_surcharge), 2) "Congestion",
          ROUND(AVG(total_amount), 2) "Total"
   FROM   v_yellow_tripdata
   GROUP BY vendor_name,
            rate_type,
            payment_type
   ORDER BY 1, 2, 3;
   ```