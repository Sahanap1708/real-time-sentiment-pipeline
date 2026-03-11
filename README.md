# Real-Time Social Media Sentiment Analysis Pipeline

## Project Overview

This project implements a **real-time data pipeline** that streams social media data, processes it for sentiment analysis, and stores the results in structured layers for analytics. The goal of the pipeline is to analyze public sentiment from social media posts and generate insights that can help in **brand monitoring and trend analysis**.

The pipeline is designed using **AWS streaming services and Databricks** to handle large volumes of incoming data efficiently. It follows a **Medallion Architecture (Bronze, Silver, Gold)** to organize raw, processed, and aggregated data for different use cases.

The project uses a dataset based on the **Twitter Sentiment Analysis Dataset from Kaggle**, which includes tweet text, user details, timestamps, and sentiment labels.

---

## Architecture Overview

The pipeline processes streaming data through the following stages:

1. Social media data is streamed through **Amazon Kinesis Data Streams**.
2. The streaming data is delivered to **Amazon S3 using Kinesis Firehose**.
3. **Databricks Structured Streaming** reads the data from the data lake.
4. Data is processed and stored in **Delta Lake tables** using Bronze, Silver, and Gold layers.
5. The processed data is used for **real-time sentiment analysis and analytics**.

---

## Data Layers

### Bronze Layer

Table: `social_catalog.raw.tweet_data`

The Bronze layer stores the **raw incoming data** exactly as it arrives from the streaming source.
This layer is used mainly for auditing and replaying the original data if required.

Key characteristics:

* Raw JSON data
* Minimal transformations
* Used as the source for downstream processing

---

### Silver Layer

Table: `social_catalog.processed.valid_tweets`

The Silver layer contains **cleaned and validated data**. Invalid records and corrupted data are filtered out at this stage.

Key transformations:

* JSON parsing using predefined schema
* Data validation and filtering
* Handling missing or invalid fields
* Standardizing data formats

---

### Gold Layer

Table: `social_catalog.analytics.sentiment_stats`

The Gold layer stores **aggregated analytical data** that can be used for dashboards or reporting.

Examples of metrics:

* Sentiment distribution (positive, negative, neutral)
* Hourly sentiment trends
* Tweet activity metrics

This layer is optimized for **analytics and business insights**.

---

## Pipeline Features

### Real-Time Streaming

The pipeline processes data using **Structured Streaming with micro-batches every 10 seconds** to ensure near real-time analysis.

### Data Quality Checks

Validation rules are applied to ensure that only valid tweets are processed and stored in the Silver layer.

### Error Handling

Streaming checkpoints and logging mechanisms are used to recover from failures and maintain pipeline stability.

### Data Governance

The project uses **Unity Catalog** to manage tables and ensure proper access control across the data platform.

### Monitoring and Alerts

Unusual sentiment patterns or anomalies can trigger alerts and are logged for further investigation.

---

## Technologies Used

* Databricks
* PySpark
* Delta Lake
* Amazon Kinesis Data Streams
* Amazon S3
* AWS Kinesis Firehose
* Python
* Pytest
* Git / GitHub
* Unity Catalog

---

## Roles and Responsibilities

* Designed and implemented a real-time social media sentiment analysis pipeline using Databricks and AWS services.
* Streamed social media data using Amazon Kinesis and delivered it to Amazon S3 through Firehose.
* Developed PySpark Structured Streaming jobs in Databricks to ingest and process streaming data.
* Implemented the Medallion Architecture (Bronze, Silver, Gold) using Delta Lake tables.
* Parsed JSON records, performed data validation, and filtered invalid data during processing.
* Implemented sentiment classification logic and created aggregated sentiment metrics.
* Configured checkpointing and error handling to ensure reliable data processing.
* Managed version control and project collaboration using Git.
* Performed data validation and testing using Pytest.

---

## Project Objective

The objective of this project is to build a **scalable and reliable real-time data pipeline** that can analyze social media sentiment and provide insights that support business decision making and brand monitoring.

---

## Outcomes

* Built a scalable streaming data pipeline using AWS and Databricks.
* Implemented structured data processing using Delta Lake architecture.
* Ensured data quality and reliability through validation and logging.
* Enabled real-time analytics for social media sentiment monitoring.

---
