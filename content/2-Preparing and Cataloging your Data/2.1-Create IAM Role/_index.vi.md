---
title: "Mẫu CloudFormation"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

## Tạo IAM role cho Data Lake

Chúng ta sẽ tạo IAM role cho các dịch vụ (Glue, QuickSight, v.v.) cần truy cập dữ liệu trong S3 và thực hiện các hành
động của nó.

1. Truy cập **[IAM Role](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/roles)** trong AWS
   Console.
2. Nhấn vào **Create role**.

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/1/21-001.png?featherlight=false&width=90pc)

3. Nhấn vào **Custom trust policy**.
4. Tin cậy QuickSight, Glue

   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Principal": {
                   "Service": "quicksight.amazonaws.com"
               },
               "Action": "sts:AssumeRole"
           },
           {
               "Effect": "Allow",
               "Principal": {
                   "Service": "glue.amazonaws.com"
               },
               "Action": "sts:AssumeRole"
           }
       ]
   }
   ```

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/1/21-002.png?featherlight=false&width=90pc) 
5. Nhấn **next**.
6. Thêm quyền (chẳng hạn như **AdministratorAccess**) 
7. Nhấn **next** cho đến trang Review. 

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/1/21-003.png?featherlight=false&width=90pc)
8. Nhấn **Create role**. 
## Tạo IAM role cho CloudFormation 
Chúng ta sẽ tạo IAM role cho CloudFormation để tạo tài nguyên 
1. Truy cập **[IAM Role](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/roles)** trong AWS Console. 
2. Nhấn vào **Create role**. 

   ![Hình ảnh](/repo_pmt_ws-fcj-004/images/2/1/21-004.png?featherlight=false&width=90pc) 
3. Trong AWS Service chọn **CloudFormation**. 
4. Nhấn **next**. 
5. Thêm quyền (chẳng hạn như **AdministratorAccess**) 
6. Nhấn **next** cho đến trang Review. 
7. Nhấn **Create role**.