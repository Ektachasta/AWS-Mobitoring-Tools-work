# 🚀 AWS Monitoring Tools: Prometheus, Grafana & ELK

## 🌟 Overview
Welcome to the **AWS Monitoring Toolkit**! This repository is your one-stop solution for setting up **Prometheus**, **Grafana**, and **ELK Stack (Elasticsearch, Logstash, Kibana)** to monitor your AWS resources effortlessly. Whether you're a DevOps enthusiast or an AWS power user, this setup will help you gain deep insights into your infrastructure with **real-time metrics, logs, and beautiful dashboards**. 📊✨

## ⚡ Features
✅ **Prometheus** - Powerful metrics collection and alerting  
✅ **Grafana** - Stunning visualizations and dashboards  
✅ **AWS Exporters** - Collect CloudWatch metrics with ease  
✅ **ELK Stack** - Centralized logging and search capabilities  
✅ **Dockerized Deployment** - Spin it up in minutes! 🚀  

## 🔧 Prerequisites
Before you begin, make sure you have:
- ✅ An **AWS account** with appropriate IAM permissions
- ✅ **Docker & Docker Compose** installed
- ✅ **AWS CLI** configured with your credentials

## 🚀 Quick Start
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/your-github-username/aws-monitoring-tools.git
cd aws-monitoring-tools
```

### 2️⃣ Configure AWS Credentials
Make sure your AWS credentials are set up properly in `~/.aws/credentials` or as environment variables:
```sh
export AWS_ACCESS_KEY_ID=your-access-key
export AWS_SECRET_ACCESS_KEY=your-secret-key
export AWS_REGION=your-region
```

### 3️⃣ Launch the Monitoring Stack
```sh
docker-compose up -d
```

### 4️⃣ Access Monitoring Tools 🖥️
- **Grafana Dashboard:** [http://localhost:3000](http://localhost:3000) (Default login: `admin` / `admin`)
- **Prometheus:** [http://localhost:9090](http://localhost:9090)
- **Elasticsearch API:** [http://localhost:9200](http://localhost:9200)
- **Kibana Dashboard:** [http://localhost:5601](http://localhost:5601)

## 🏗️ Components Breakdown
### **📡 Prometheus** (Port: `9090`)
- Collects and stores metrics from AWS and system exporters
- Configurations are managed via `prometheus.yml`

### **📊 Grafana** (Port: `3000`)
- Pre-configured AWS monitoring dashboards
- Stunning visualizations for better insights

### **☁️ AWS Exporters**
- `prometheus-node-exporter` for system metrics
- `cloudwatch-exporter` to fetch AWS CloudWatch metrics

### **📜 ELK Stack (Elasticsearch, Logstash, Kibana)**
#### 🔍 **Elasticsearch** (Port: `9200`)
- Distributed search and analytics engine
- Stores and indexes logs for quick retrieval

#### 📥 **Logstash**
- Collects, processes, and sends logs to Elasticsearch
- Supports various input sources (AWS logs, system logs, etc.)

#### 📊 **Kibana** (Port: `5601`)
- Provides an intuitive UI to analyze logs and metrics
- Customizable dashboards for real-time monitoring

## 📈 What Can You Monitor?
### **🖥️ EC2 Instances**
✅ CPU Utilization  
✅ Network Traffic  
✅ Disk Read/Write  

### **📦 S3 Buckets**
✅ Storage Size  
✅ Request Count  

### **🛢️ RDS Databases**
✅ CPU Usage  
✅ Active Connections  

### **📑 Logs with ELK**
✅ Application Logs  
✅ System Logs  
✅ AWS CloudWatch Logs  

---
Happy Monitoring! 📊🚀
