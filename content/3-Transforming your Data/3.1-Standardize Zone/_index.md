---
title: "Transform to Standardize Zone"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

## Planning the Data Transformation Steps

It’s a good practice to plan the steps to transform your data. Based on the information we captured during data
exploration stage, we can come up with the following transformation step:

1. Read raw data from S3.
2. Perform data transformation: Set appropriate data types.
3. Save processed dataset to S3 in a query optimized format.
4. Run crawlers to create tables
5. Query transformed data in Athena

## Create Raw to Standardize Glue job

1. Go to Glue console.
2. In the left navigation panel, click **ETL jobs**.
3. On the AWS Glue Studio page, click **Visual ETL**.

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-001.png?featherlight=false&width=90pc)

### taxi_zone_lookup

1. Adding Yellow Trips data from Amazon S3
    * Click on the Source icon, choose **S3**.
    * In the **Data source – S3 bucket node**, to specify the following information:
        * S3 URL: `S3://{RAW_BUCKET}/nyc-taxi/taxi_zone_lookup/`

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-002.png?featherlight=false&width=90pc)

2. Modify data types
    * Click on the **Transform** icon, choose **Change Schema**.
    * Change data type

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-003.png?featherlight=false&width=90pc)

3. Save transformed data to Amazon S3
    * Click on the Target icon, choose Amazon S3.
    * Specify the following information
        * **Format** – Parquet
        * **Compression Type** - Snappy
        * S3 Target Location `S3://{Standardize_BUCKET}/taxi_zone_lookup/`

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-004.png?featherlight=false&width=90pc)

4. Set job detail
    * Specify Iam role

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-005.png?featherlight=false&width=90pc)

5. Run job
    * Click **Run**.

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-006.png?featherlight=false&width=90pc)

6. Check output
    * Go to **standardize bucket** in S3 console.

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-007.png?featherlight=false&width=90pc)

### yellow_tripdata

1. Adding Yellow Trips data from Amazon S3
    * Click on the Source icon, choose **S3**.
    * In the **Data source – S3 bucket node**, to specify the following information:
        * S3 URL: `S3://{RAW_BUCKET}/nyc-taxi/yellow_tripdata/`

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-008.png?featherlight=false&width=90pc)

2. Modify data types
    * Click on the **Transform** icon, choose **Change Schema**.
    * Change data type

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-009.png?featherlight=false&width=90pc)

3. Save transformed data to Amazon S3
    * Click on the Target icon, choose Amazon S3.
    * Specify the following information
        * **Format** – Parquet
        * **Compression Type** - Snappy
        * S3 Target Location `S3://{Standardize_BUCKET}/yellow_tripdata/`

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-010.png?featherlight=false&width=90pc)

4. Set job detail
    * Specify Iam role

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-005.png?featherlight=false&width=90pc)

5. Run job
    * Click **Run**.

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-011.png?featherlight=false&width=90pc)

6. Check output
    * Go to **standardize bucket** in S3 console.

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-012.png?featherlight=false&width=90pc)

## Run Crawlers to create Tables

1. Go to the AWS Glue Console.
2. In the left navigation menu, click **Crawlers**.
3. On the Crawlers page, select your crawler, and then click **Run crawler**.

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-013.png?featherlight=false&width=90pc)
4. In the left navigation menu, click **Tables**.

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-014.png?featherlight=false&width=90pc)
5. On the Tables page, click on **table name** to review the table metadata and schema information.

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-015.png?featherlight=false&width=90pc)

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-016.png?featherlight=false&width=90pc)

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-017.png?featherlight=false&width=90pc)

## Query transformed data in Athena

### Using Amazon Athena for the first time

Amazon Athena automatically stores query results and metadata information for each query that runs in a query result
location that you can specify in Amazon S3. If necessary, you can access the files in this location to work with them.
You can also download query result files directly from the Athena console.

1. Go to Athena console. Click **Get Started**

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-018.png?featherlight=false&width=90pc)
2. Choose **Edit Settings**, click on **Browse S3** and select bucket as the value for the Location of query result -
   optional field.

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-019.png?featherlight=false&width=90pc)

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-020.png?featherlight=false&width=90pc)
3. Go to the top menu, click on **Editor** to return back to the Query editor page.

### Query Standardize data

1. Choose **database**
2. Choose **table**
3. Choose **preview table**

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-021.png?featherlight=false&width=90pc)

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-022.png?featherlight=false&width=90pc)