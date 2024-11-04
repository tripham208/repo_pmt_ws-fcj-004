---
title: "Create Crawler"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.4 </b> "
---

Glue Crawler is a feature that automatically infer database and table schema from your source data then stores the
associated metadata in the AWS Glue Data Catalog.

## Create Crawler for **taxi_zone_lookup** table

1. Go to the AWS Glue Console.
2. In the left navigation menu, click **Crawlers**.
3. On the Crawlers page, click **Create a crawler**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/4/24-001.png?featherlight=false&width=90pc)

4. Specify crawler’s name, click **Next**.
5. On the Choose data sources and classifiers screen, specify the following information, and then click **Next**.

    * Click **Add a data source**
    * Choose a Data source – **S3**
    * Select Location of S3 data - **In this account**
    * Include S3 path – s3://{Standardize_BUCKET}/taxi_zone_lookup/
    * For Subsequent crawler runs, select to Crawl all sub-folders
    * Then click Add an S3 data source.

6. On Configure security settings, choose your datalake role from the Existing IAM role, click **Next**.
7. Choose  **your Standardize** database.
8. On the Crawler schedule, leave the frequency **On demand**, click **Next**.
9. Review the crawler details, click **Create crawler**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/4/24-002.png?featherlight=false&width=90pc)

## Create Crawler for **yellow_tripdata** table

1. Go to the AWS Glue Console.
2. In the left navigation menu, click **Crawlers**.
3. On the Crawlers page, click **Create a crawler**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/4/24-001.png?featherlight=false&width=90pc)

4. Specify crawler’s name, click **Next**.
5. On the Choose data sources and classifiers screen, specify the following information, and then click **Next**.

    * Click Add a data source
    * Choose a Data source – **S3**
    * Select Location of S3 data - **In this account**
    * Include S3 path – s3://{Standardize_BUCKET}/yellow_tripdata/
    * For Subsequent crawler runs, select to Crawl all sub-folders
    * Then click Add an S3 data source.

6. On Configure security settings, choose your datalake role from the Existing IAM role, click **Next**.
7. Choose  **your Standardize** database.
8. On the Crawler schedule, leave the frequency **On demand**, click **Next**.
9. Review the crawler details, click **Create crawler**.

   ![Image](/repo_pmt_ws-fcj-004/images/2/4/24-003.png?featherlight=false&width=90pc)
