---
title: "Create IAM Role"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

## Create IAM role Data Lake

We will create Iam role for services( Glue, QuickSight,etc.) need access data in S3, perform its action.

1. Go to **[IAM Role](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/roles)** in AWS Console.
2. Click **Create role**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/1/21-001.png?featherlight=false&width=90pc)

3. Click **Custom trust policy**.
4. Trust QuickSight, Glue

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

   ![Image](/repo_pmt_ws-fcj-004/images/2/1/21-002.png?featherlight=false&width=90pc)

5. Click **next**.
6. Add permission (like **AdministratorAccess**)
7. Click **next** until Review page.

   ![Image](/repo_pmt_ws-fcj-004/images/2/1/21-003.png?featherlight=false&width=90pc)
8. Click **Create role**.

## Create IAM role for CloudFormation

We will create Iam role for CloudFormation to create resource

1. Go to **[IAM Role](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/roles)** in AWS Console.
2. Click **Create role**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/1/21-004.png?featherlight=false&width=90pc)

3. In AWS Service choose **CloudFormation**.
4. Click **next**.
5. Add permission (like **AdministratorAccess**)
6. Click **next** until Review page.
7. Click **Create role**.
