---
title: "Visualizing your Data"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 5. </b> "
---

## Using Amazon QuickSight for the first time

1. Go to QuickSight console, click Sign up for QuickSight.

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-001.png?featherlight=false&width=90pc)
2. On the Create your QuickSight account page, specify the following
    * QuickSight account name
    * Notification email address
    * Authentication method

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-002.png?featherlight=false&width=90pc)
3. Choose your exist IAM role

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-003.png?featherlight=false&width=90pc)
4. On the Create your QuickSight account page, click Finish

## Connect to a data source

1. On the QuickSight page, click **Datasets** in the left navigation menu pane.
2. On the upper right section of the screen, click **new dataset**
3. Select **Athena**
4. In the New Athena data source window, specify the following:

    * Data source name
    * Athena workgroup – primary
    * Click **Create Data Source**

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-004.png?featherlight=false&width=90pc)

5. In the Choose your table window, specify the following:
    * Catalog – AwsDataCatalog
    * Database
    * Tables – v_yellow_tripdata

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-005.png?featherlight=false&width=90pc)

6. In the Finish dataset creation window, specify the following:
7. Import to SPICE for quicker analytics

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-006.png?featherlight=false&width=90pc)

## Visualize your data

1. QuickSight will attempt to load your data to SPICE, please wait for a few minutes.
2. To visualize the flow of yellow taxi trips from pickup borough to drop-off borough, click + Add in the menu.
3. Select the **Sankey** visual type, specify the following on the Field wells.

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-007.png?featherlight=false&width=90pc)
    * Source – pu_borough
    * Destination – do_borough
    * You can click on the visual type title, change it to Taxi Trips Flow

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-008.png?featherlight=false&width=90pc)

## Filtering Data

1. Create a filter focus on taxi trips originating from Manhattan.
2. Type **pu_borough** and then select it.
3. Click on the menu besides the **pu_borough** filter, select **Edit**.

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-009.png?featherlight=false&width=90pc)
4. Deselect **Manhattan** from the Filter list, click **Apply**.

   ![Image](/repo_pmt_ws-fcj-004/images/5/5-010.png?featherlight=false&width=90pc)
5. Get insights by examining the taxi trip flow based on pickup borough and drop-off borough.
6. Observe the traffic flow patterns.