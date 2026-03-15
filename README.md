# Real-Time-Social-Media-Sentiment-Analysis-Pipeline

Project Overview

This project implements a Real-Time Social Media Sentiment Analysis Data Pipeline using modern Data Engineering architecture (Medallion Architecture).

The pipeline ingests social media data, processes it through Bronze, Silver, and Gold layers, performs sentiment analysis, and generates analytics datasets used for dashboards.

It demonstrates how a scalable and production-ready data pipeline can be built using Databricks, PySpark, AWS, and orchestration tools.

---

Architecture

                +---------------------+
                |      AWS S3         |
                |   Raw Data Source   |
                +----------+----------+
                           |
                           v
                +---------------------+
                |   Bronze Layer      |
                | Raw Data Ingestion  |
                +----------+----------+
                           |
                           v
                +---------------------+
                |   Silver Layer      |
                | Data Cleaning &     |
                | Transformation      |
                +----------+----------+
                           |
                           v
                +---------------------+
                |    Gold Layer       |
                | Analytics Tables    |
                +----------+----------+
                           |
                           v
                +---------------------+
                | Databricks SQL      |
                | Dashboards          |
                +----------+----------+
                           |
                           v
                +---------------------+
                | Slack Notifications |
                | Alerts & Monitoring |
                +---------------------+

Pipeline orchestration is handled through Apache Airflow, which schedules and monitors the workflow.

---

Technology Stack

Technology| Purpose
Databricks| Data processing and analytics
PySpark| Distributed data transformation
Delta Lake| Data storage format
AWS S3| Data storage
SQL| Analytics queries
Python| Pipeline development
GitHub| Version control
Databricks Dashboards| Data visualization
Apache Airflow| Pipeline orchestration
Slack Webhooks| Alerting & monitoring

---

Data Pipeline Layers

Bronze Layer

Purpose: Store raw ingested data.

Tables:

- tweets_table
- sentiment_table
- trends_table
- user_metadata_table
- valid_table

Operations:

- Ingest raw data from S3
- Store raw records without modification
- Maintain original schema

Folder:

bronze_layer/

---

Silver Layer

Purpose: Perform data cleaning and validation.

Transformations:

- Remove null values
- Remove duplicates
- Trim spaces
- Convert timestamp formats
- Schema validation

Output tables:

- silver.tweets_table
- silver.sentiment_table
- silver.trends_table
- silver.user_metadata_table
- silver.valid_table

Folder:

silver_layer/

---

Gold Layer

Purpose: Generate analytics-ready tables.

Tables created:

- fact_tweet
- fact_trend
- dim_user
- dim_topic
- dim_country
- agg_sentiment_by_topic
- agg_user_influence

These tables power the analytics dashboards.

Folder:

gold_layer/

---

Analytics Layer

The analytics layer prepares datasets used in dashboards.

Examples:

- Sentiment distribution
- Tweets by topic
- Tweets over time
- Top influencers
- Trending topics by country

Folder:

analytics/

Notebook:

dashboard_queries

---

Dashboard Metrics

Tweets Metrics

- Total tweets count
- Tweets per topic
- Tweets over time
- Average likes per tweet
- Average retweets per tweet

Sentiment Metrics

- Positive tweets
- Negative tweets
- Neutral tweets
- Sentiment distribution
- Average sentiment score

Trend Metrics

- Top trending topics
- Trend popularity by location
- Trend growth over time

User Metrics

- Top influencers by followers
- Average followers per user
- User engagement activity

Valid Tweet Metrics

- Valid tweet count
- Engagement metrics
- Topic-wise tweet validation

---

Pipeline Orchestration (Apache Airflow)

The pipeline is orchestrated using Apache Airflow DAGs.

Airflow schedules the pipeline to execute tasks sequentially:

Bronze Ingestion
      ↓
Silver Transformation
      ↓
Gold Aggregations
      ↓
Analytics Dataset Generation
      ↓
Dashboard Refresh

Benefits:

- Automated scheduling
- Workflow monitoring
- Failure handling
- Retry mechanisms

---

Slack Alerting System

Slack notifications are integrated to monitor pipeline health.

Alerts include:

- Pipeline success notifications
- Pipeline failure alerts
- Data anomaly detection
- Processing errors

Example Slack alert:

Pipeline Status: SUCCESS
Dataset: Tweets Data
Processed Records: 10,245
Timestamp: 2026-03-15

Alerts are triggered using Slack Webhook integration.

---

Repository Structure

Real-Time-Social-Media-Sentiment-Analysis-Pipeline
│
├── bronze_layer
│   └── bronze_pipeline
│
├── silver_layer
│   └── silver_pipeline
│
├── gold_layer
│   └── gold_pipeline
│
├── analytics
│   └── dashboard_queries
│
├── airflow
│   └── sentiment_pipeline_dag.py
│
└── README.md

---

Sample Data

Dataset used:

Twitter Sentiment Analysis Dataset

Fields include:

- tweet_id
- user_id
- tweet_text
- timestamp
- impressions
- likes
- retweets
- replies
- sentiment_score

---

Key Features

- Medallion Architecture (Bronze → Silver → Gold)
- Data Quality Validation
- Distributed Data Processing using PySpark
- Automated Workflow Scheduling (Airflow)
- Slack Alert Monitoring
- Analytics Dashboards
- Version Control with GitHub

---

Future Enhancements

- Real-time streaming ingestion (Kafka/Kinesis)
- Machine learning sentiment classification
- Automated CI/CD pipelines
- Advanced anomaly detection
- Real-time dashboards

---

Author

Samagna Pinnamreddy
Data Engineering Project – Real-Time Social Media Sentiment Analysis
