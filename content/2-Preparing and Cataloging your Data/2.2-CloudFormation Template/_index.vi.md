---
title: "Mẫu CloudFormation"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

## Triển khai Mẫu CloudFormation

Đầu tiên chúng ta sẽ thiết lập các tài nguyên cần thiết cho bài thực hành này. Chúng ta sẽ tạo các S3 bucket để lưu trữ các tệp tin và các IAM role phù hợp cho các dịch vụ mà chúng ta sẽ sử dụng. Các tài nguyên này đã được định nghĩa trong một mẫu CloudFormation.

1. Truy cập **CloudFormation** trong AWS Console.
2. Trong menu điều hướng bên phải, nhấn vào **Create stack, With new resources (standard)**.
3. Tải xuống tệp này: [CF Template](/repo_pmt_ws-fcj-004/resources/CF_template.yaml)
4. Chọn **Upload a template file**, và tải lên tệp bạn đã tải xuống.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2/22-001.png?featherlight=false&width=90pc)

   Bạn có thể xem trước trong **View in Infrastructure Compose**
    - 3 S3 bucket
    - 2 Glue Database

      ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2/22-002.png?featherlight=false&width=90pc)

5. Nhấn **next**.
6. Đối với stack name, chỉ định **StackName** của bạn.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2/22-003.png?featherlight=false&width=90pc)

7. Nhấn **next**. Chọn Iam role của bạn

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2/22-004.png?featherlight=false&width=90pc)

8. Nhấn **next** cho đến trang Review.
9. Nhấn **Submit**. Đợi các tài nguyên được cung cấp.

## Kiểm tra tài nguyên đã triển khai

- 2 Glue Database

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2/22-005.png?featherlight=false&width=90pc)

- 3 S3 bucket

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/2/22-006.png?featherlight=false&width=90pc)
