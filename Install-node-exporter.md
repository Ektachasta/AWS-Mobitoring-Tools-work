# 🖥️ Install Node Exporter

## 📖 Overview
Node Exporter is a Prometheus exporter for hardware and OS metrics, allowing you to monitor system performance efficiently. This guide provides step-by-step instructions to install and configure Node Exporter.

## 🔧 Installing Node Exporter

### 1️⃣ Create a Dedicated User
To improve security, create a system user for Node Exporter:
```sh
sudo useradd --system --no-create-home --shell /bin/false node_exporter
```

### 2️⃣ Download Node Exporter
Fetch the latest Node Exporter package:
```sh
wget https://github.com/prometheus/node_exporter/releases/download/v1.6.1/node_exporter-1.6.1.linux-amd64.tar.gz
```

### 3️⃣ Extract and Move Node Exporter Files
```sh
tar -xvf node_exporter-1.6.1.linux-amd64.tar.gz
sudo mv node_exporter-1.6.1.linux-amd64/node_exporter /usr/local/bin/
rm -rf node_exporter*
```

## ⚙️ Configuring Node Exporter as a System Service

### 1️⃣ Create a Systemd Service File
Open the Node Exporter service file:
```sh
sudo vim /etc/systemd/system/node_exporter.service
```

### 2️⃣ Add the Following Configuration:
```ini
[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=node_exporter
Group=node_exporter
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
```

### 3️⃣ Enable and Start Node Exporter
```sh
sudo systemctl enable node_exporter
sudo systemctl start node_exporter
```

### 4️⃣ Verify Node Exporter Status
```sh
sudo systemctl status node_exporter
```

## 🌍 Configuring Prometheus to Scrape Node Exporter Metrics
Add the following job to your Prometheus configuration (`prometheus.yml`):
```yaml
- job_name: "node_exporter"
  static_configs:
    - targets: ["<your-server-ip>:9100"]
- job_name: "node_exporter"
  static_configs:
    - targets: ["localhost:9100"]
    
```

## 🔗 Accessing Node Exporter Metrics
Once Node Exporter is running, you can access its metrics at:
```
http://<your-server-ip>:9100/metrics
```

## Node Exporter UI

After setting up Node Exporter, you can access its web interface at:

[http://your-server-ip:9100](http://your-server-ip:9100)

Here is a screenshot of the Node Exporter interface:

![Node Exporter UI](https://imgur.com/n6pzbRA.png)

---

Node Exporter is now successfully set up and ready to provide system metrics to Prometheus! 🚀
