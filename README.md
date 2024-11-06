# Stock Market Analysis in AWS

## Table of Contents 📋
- [Overview](#overview)
- [Installation](#installation)
- [Challenges](#challenges)
- [Points to Improve](#points-to-improve)
- [Tools](#tools)
- [Architecture](#architecture)
- [Contact](#contact)

---

## 🚀 Overview

This project aims to perform **real-time stock market analysis** using various **AWS services**. By integrating **Kafka**, **S3**, **AWS Crawler**, **Glue Data Catalog**, and **Athena**, the project facilitates efficient data streaming, processing, and querying for stock market data at scale. It allows you to analyze live stock market data streams, store the data in **S3** for future use, and use **AWS Crawler** for automatically discovering and cataloging the data, making it easier to query and analyze stock data in real time.

### Key Features:
- **Real-time stock market data collection** using **Kafka** for streaming data ingestion.
- **AWS S3** for scalable storage of raw and processed stock market data.
- **AWS Crawler** for data discovery and automatic cataloging in the **Glue Data Catalog**.
- **Glue Data Catalog** to maintain a catalog of stock data for easier querying and metadata management.
- **AWS Athena** for querying the stock data directly from **S3** using SQL without the need for data movement.
- Scalable and serverless architecture for processing large volumes of stock data.


---


## ⚙️ Installation

Follow the steps below to set up the project on your local machine or AWS environment.

### Prerequisites:
- **AWS Account**: Make sure you have an active AWS account. If not, you can create one [here](https://aws.amazon.com/).
- **AWS CLI**: Install and configure the AWS Command Line Interface (CLI) for interacting with AWS services. [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- **Git**: Make sure you have Git installed to clone the repository.

### 1. **Clone the repository**:
Clone the project repository to your local machine using the following command:

```bash
git clone git@github.com:Samiha128/Live-Analysis-of-Stock-Market-Data-on-AWS.git
cd Live-Analysis-of-Stock-Market-Data-on-AWS

