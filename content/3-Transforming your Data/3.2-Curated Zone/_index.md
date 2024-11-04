---
title: "Transform to Curated Zone"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 3.2 </b> "
---

## Planning the Data Transformation Steps

It’s a good practice to plan the steps to transform your data. Based on the information we captured during data
exploration stage, we can come up with the following transformation step:

1. Read standardized data from S3.
2. Perform data transformation: Join yellow_tripdata table with taxi_zone_lookup to get location pick up, location drop
   off
3. Save processed dataset to S3 in a query optimized format.
4. Query transformed data in Athena

## Create Standardize to Curated Glue job

1. Go to Glue console.
2. In the left navigation panel, click **ETL jobs**.
3. On the AWS Glue Studio page, click **Visual ETL**.

   ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-001.png?featherlight=false&width=90pc)

4. Adding taxi_zone_lookup pickup from Glue Data Catalog
    * Click on the Source icon, choose **Glue Data Catalog**.
    * Choose your **Standardize database** and **taxi_zone_lookup** table
    * Rename node with suffix **pickup**

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-001.png?featherlight=false&width=90pc)

5. Adding yellow_tripdata from Glue Data Catalog
    * Click on the Source icon, choose **Glue Data Catalog**.
    * Choose your **Standardize database** and **yellow_tripdata** table

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-002.png?featherlight=false&width=90pc)

6. Modify column name of taxi_zone_lookup pickup
    * Choose node taxi_zone_lookup pickup
    * Click on the **Transform** icon, choose **Change Schema**.
    * Change column name with prefix **pu**

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-003.png?featherlight=false&width=90pc)

7. Join yellow_tripdata with taxi_zone_lookup pickup transformed
    * Choose node yellow_tripdata
    * Click on the **Transform** icon, choose **Join**.
    * Update node parent
    * Rename node with suffix **pickup**
    * Under the Join conditions, select the following keys:
        * **taxi_zone_lookup pickup** - pu_location_id
        * **yellow_tripdata** - pulocationid

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-004.png?featherlight=false&width=90pc)

8. Adding taxi_zone_lookup drop off from Glue Data Catalog
    * Click on the Source icon, choose **Glue Data Catalog**.
    * Choose your **Standardize database** and **taxi_zone_lookup** table
    * Rename node with suffix **dropoff**

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-005.png?featherlight=false&width=90pc)

9. Modify column name of taxi_zone_lookup drop off
    * Choose node taxi_zone_lookup dropoff
    * Click on the **Transform** icon, choose **Change Schema**.
    * Change column name with prefix **do**

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-006.png?featherlight=false&width=90pc)

10. Join taxi_zone_lookup drop off transformed
    * Choose node **join pickup**
    * Click on the **Transform** icon, choose **Join**.
    * Update node parent
    * Under the Join conditions, select the following keys:
        * **taxi_zone_lookup dropoff** - do_location_id
        * **yellow_tripdata** - dolocationid

    ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-007.png?featherlight=false&width=90pc)

11. Save transformed data to Amazon S3
    * Click on the Target icon, choose Amazon S3.
    * Specify the following information
        * **Format** – Iceberg
        * **Compression Type** - GZIP
        * S3 Target Location `S3://{Curated_BUCKET}/`
        * Choose your **Curated database** and enter **yellow_tripdata** table

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-008.png?featherlight=false&width=90pc)
    * Review diagram

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-009.png?featherlight=false&width=90pc)

12. Set job detail
    * Specify Iam role

      ![Image](/repo_pmt_ws-fcj-004/images/3/1/31-005.png?featherlight=false&width=90pc)

13. Run job
    * Click **Run**.

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-010.png?featherlight=false&width=90pc)
    * Check log.

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-011.png?featherlight=false&width=90pc)

    * Check metrics

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-012.png?featherlight=false&width=90pc)

14. Check output
    * Go to **standardize bucket** in S3 console.

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-013.png?featherlight=false&width=90pc)

### Query Curated data

1. Choose your **Curated**
2. Choose **yellow_tripdata**
3. Choose **preview table**

   ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-016.png?featherlight=false&width=90pc)
4. Review schema
    * Choose **yellow_tripdata**
    * Click **View in glue**
   
      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-014.png?featherlight=false&width=90pc)

      ![Image](/repo_pmt_ws-fcj-004/images/3/2/32-015.png?featherlight=false&width=90pc)
