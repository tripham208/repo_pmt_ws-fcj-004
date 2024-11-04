---
title: "Preparing your Data"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

## Upload raw data

We will upload data in CSV format to S3 Raw bucket

* taxi_zone_lookup: data about the locations of trips
* yellow_tripdata: trip information data

1. Go to **S3 Raw bucket** in AWS Console.
2. Create **taxi_zone_lookup** and **yellow_tripdata** folders

   ![Image](/repo_pmt_ws-fcj-004/images/2/3/23-001.png?featherlight=false&width=90pc)

3. Download this
   files: [taxi_zone_lookup](/repo_pmt_ws-fcj-004/resources/taxi_zone_lookup.csv), [yellow_tripdata](/repo_pmt_ws-fcj-004/resources/yellow_tripdata_2020-04.csv)
4. Upload [taxi_zone_lookup](/repo_pmt_ws-fcj-004/resources/taxi_zone_lookup.csv) to **taxi_zone_lookup** folder
5. Upload [yellow_tripdata](/repo_pmt_ws-fcj-004/resources/yellow_tripdata_2020-04.csv) to **yellow_tripdata** folder

   ```
      raw-bucket/
      |---------nyc-taxi/
      |-----------------taxi_zone_lookup/taxi_zone_lookup.csv
      |-----------------yellow_tripdata/yellow_tripdata.csv
   ```