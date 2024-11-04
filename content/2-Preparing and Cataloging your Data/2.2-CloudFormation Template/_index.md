---
title: "CloudFormation Template"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

## Deploy a CloudFormation Template

We will first set up required resources for this lab. We will be creating S3 buckets to store the files and appropriate
IAM roles for the services that we will be using. These resources are been defined in a CloudFormation template.

1. Go to **CloudFormation** in AWS Console.
2. In the right navigation menu, click **Create stack, With new resources (standard)**.
3. Download this file: [CF Template](/repo_pmt_ws-fcj-004/resources/CF_template.yaml)
4. Select **Upload a template file**, and upload the file you downloaded.

   ![Image](/repo_pmt_ws-fcj-004/images/2/2/22-001.png?featherlight=false&width=90pc)

   You can preview in **View in Infrastructure Compose**
    - 3 S3 bucket
    - 2 Glue Database

      ![Image](/repo_pmt_ws-fcj-004/images/2/2/22-002.png?featherlight=false&width=90pc)

5. Click **next**.
6. For stack name, specify your **StackName**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/2/22-003.png?featherlight=false&width=90pc)

7. Click **next**. Choose your Iam role

   ![Image](/repo_pmt_ws-fcj-004/images/2/2/22-004.png?featherlight=false&width=90pc)

8. Click **next** until Review page.
9. Click **Submit**. Wait for resources to be provisioned.

## Check resource deployed

- 2 Glue Database

   ![Image](/repo_pmt_ws-fcj-004/images/2/2/22-005.png?featherlight=false&width=90pc)

- 3 S3 bucket

   ![Image](/repo_pmt_ws-fcj-004/images/2/2/22-006.png?featherlight=false&width=90pc)


