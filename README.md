# Stock Market Analysis in AWS

## Table of Contents 📋
- [Overview](#overview)
- [Installation](#installation)
- [Challenges](#challenges)
- [Points to Improve](#points-to-improve)
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

### 2. Set up AWS services:
   This project leverages several AWS services. Here's how to set them up:
   
#### EC2 Instance Setup:

  Create an EC2 instance:
  Launch an EC2 instance in your desired AWS region (preferably t2.micro for Free Tier usage).
#### Connect to your EC2 instance:

Use SSH to connect to your instance:

    ```bash
     ssh -i "path/to/your/file.pem" ec2-user@<your-ec2-public-ip>


#### Installing Kafka on EC2

1. **Download and extract Kafka**:

    ```bash
    wget https://archive.apache.org/dist/kafka/3.6.1/kafka_2.12-3.6.1.tgz
    tar -xvf kafka_2.12-3.6.1.tgz
    cd kafka_2.12-3.6.1
    ```

2. **Install Java** (Kafka requires Java 17 or above):

    ```bash
    sudo yum install java-17-amazon-corretto
    java -version
    ```

3.**Starting Zookeeper and Kafka:**
  ```bash
       bin/zookeeper-server-start.sh config/zookeeper.properties

  ```
In a new terminal session, start the Kafka server:
  ```bash
       export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
       cd kafka_2.12-3.6.1
       bin/kafka-server-start.sh config/server.properties


  ```
Note: You may need to modify the server.properties file to set your EC2's public IP address. 
   ```bash
       sudo nano config/server.properties

  ```
Change the line for ADVERTISED_LISTENERS to your EC2 instance's public IP address:

```bash
      ADVERTISED_LISTENERS=PLAINTEXT://your-ec2-public-ip:9092
  ```
4.**Creating a Kafka Topic:**

In a new terminal session, create a Kafka topic for stock market data:
```bash
      cd kafka_2.12-3.6.1
     bin/kafka-topics.sh --create --topic stock_market_data --bootstrap-server your-ec2-public-ip:9092 --replication-factor 1 --partitions 1

  ```
5.**Starting Producer and Consumer:**
Start a producer to simulate sending stock market data:
```bash
     bin/kafka-console-producer.sh --topic stock_market_data --bootstrap-server your-ec2-public-ip:9092

  ```
Start a consumer to listen to the topic:
```bash
     bin/kafka-console-consumer.sh --topic stock_market_data --bootstrap-server your-ec2-public-ip:9092

  ```
