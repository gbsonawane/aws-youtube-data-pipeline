# 🎥 AWS YouTube Data Engineering Pipeline

An end-to-end data engineering pipeline that ingests YouTube data,
stores raw data in Amazon S3, transforms the data into analytics-ready
Parquet files, and prepares it for downstream analysis.

## 🚀 Project Overview

This project demonstrates how to build a scalable and automated
data pipeline using AWS services.

The pipeline collects YouTube data through the YouTube API and
processes the data through multiple stages:

YouTube API → AWS Lambda → S3 Bronze → AWS Glue → S3 Silver → 
S3 Gold → Analytics

The project follows a layered data architecture to separate
raw, cleaned, and analytics-ready data.

---

## 🏗️ Architecture

```text
                    ┌───────────────┐
                    │  YouTube API  │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ AWS Lambda    │
                    │  Ingestion    │
                    └───────┬───────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │    S3 Bronze Layer  │
                 │     Raw Data        │
                 └──────────┬──────────┘
                            │
                            ▼
                    ┌───────────────┐
                    │   AWS Glue    │
                    │ Transformation│
                    └───────┬───────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │    S3 Silver Layer │
                 │ Cleaned / Parquet  │
                 └──────────┬──────────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ AWS Glue Jobs │
                    │ Aggregations  │
                    └───────┬───────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │     S3 Gold Layer  │
                 │ Analytics Ready    │
                 └─────────────────────┘
