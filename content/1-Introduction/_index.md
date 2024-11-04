---
title: "Introduction"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

## What is a data lake?

A data lake is a centralized repository that allows you to store all your structured and unstructured data at any scale.
You can store your data as-is, without having to first structure the data, and run different types of analytics—from
dashboards and visualizations to big data processing, real-time analytics, and machine learning to guide better
decisions.

## Overview workshop

In this workshop, we will store data in S3 and use Glue transform data. Then use Athena to Analyze and visualize it in
Quicksight. We use dataset about **NYC Yellow Trips**

* Upload raw data(CSV) to Raw zone in [Amazon S3](https://aws.amazon.com/vi/s3)
* Use [AWS Glue](https://aws.amazon.com/vi/glue/) transform data from Raw zone to Standardize zone and save it
  in [Parquet](https://parquet.apache.org/) format. Data in this format, we will need create Crawler to create table and
  read data in Glue Catalog, Athena
* Use [AWS Glue](https://aws.amazon.com/vi/glue/) transform data from Standardize zone to Curated zone with more complex
  transform and save it in [Iceberg](https://iceberg.apache.org/) format
* For analyze transformed data, we will use [Amazon Athena](https://aws.amazon.com/vi/athena/)
* For visualize analyzed data, we will use [Amazon QuickSight](https://aws.amazon.com/vi/quicksight/)

![Image](/repo_pmt_ws-fcj-004/images/001.png?featherlight=false&width=90pc)

## Introducing Amazon S3

Amazon Simple Storage Service (S3) is the largest and most performant object storage service for structured and
unstructured data and the storage service of choice to build a data lake. With Amazon S3, you can cost-effectively build
and scale a data lake of any size in a secure environment where data is protected by 99.999999999% (11 9s) of
durability.

With data lakes built on Amazon S3, you can use native AWS services to run big data analytics, artificial intelligence (
AI) and Machine Learning (ML) to gain insights from your unstructured data sets. Data can be collected from multiple
sources and moved into the data lake in its original format. It can be accessed or processed with your choice of
purpose-built AWS analytics tools and frameworks. Making it easy and quick to run analytics without the need to move
your data to a separate analytics system.

## Introducing AWS Glue

AWS Glue is a fully managed serverless extract, transform, and load (ETL) service that makes it simple and cost-effective to categorize your data, clean it, enrich it, and move it reliably between various data stores. AWS Glue consists of the following core components:

* Data Catalog – a central repository to store structural and operational metadata of your data assets.
* ETL Engine – automatically generate Scala or Python code.
* Jobs System – provides managed infrastructure to orchestrate your ETL workflow.

AWS Glue also includes additional components like:

* [AWS Glue DataBrew](https://aws.amazon.com/glue/features/databrew/)  - A visual data preparation tool that makes it easy for data analysts and data scientists to prepare data with an interactive, point-and-click visual interface without writing code.
* [AWS Glue Elastic Views](https://aws.amazon.com/glue/)  - Build materialized views that combine and replicate data across multiple data stores without you having to write custom code.
*  AWS Glue Studio is a graphical interface that makes it easy to create, run, and monitor extract, transform, and load (ETL) jobs in AWS Glue. You can visually compose data transformation workflows, AWS Glue studio will generate Apache Spark code on your behalf, and let it seamlessly run them on AWS Glue’s Apache Spark-based serverless ETL engine.

Together, these automate much of the undifferentiated heavy lifting involved with discovering, categorizing, cleaning, enriching, and moving data, so you can spend more time analyzing your data.

## Introducing Amazon Athena

Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. Athena
is serverless, so there is no infrastructure to manage, and you pay only for the queries that you run. Athena is easy to
use. Simply point to your data in Amazon S3, define the schema, and start querying using standard SQL. Most results are
delivered within seconds. With Athena, there’s no need for complex ETL jobs to prepare your data for analysis. This
makes it easy for anyone with SQL skills to quickly analyze large-scale datasets. Athena is out-of-the-box integrated
with AWS Glue Data Catalog, allowing you to create a unified metadata repository across various services, crawl data
sources to discover schemas and populate your Catalog with new and modified table and partition definitions, and
maintain schema versioning.

## Introducing Amazon QuickSight

Amazon QuickSight is a scalable, serverless, embeddable, machine learning (ML)-powered business intelligence (BI)
service built for the cloud. It enables you to create and publish interactive dashboards and highly formatted reports
accessible through web browsers or mobile devices. 