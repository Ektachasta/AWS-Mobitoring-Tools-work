# 📡 Install Prometheus

## 📖 Overview
This guide provides step-by-step instructions to install and configure **Prometheus** for monitoring your applications.

## 🔧 Installing Prometheus

### 1️⃣ Create a Dedicated Prometheus User
Run the following command to create a system user for Prometheus:
```sh
sudo useradd --system --no-create-home --shell /bin/false prometheus
```

### 2️⃣ Download Prometheus
Fetch the latest Prometheus package:
```sh
wget https://github.com/prometheus/prometheus/releases/download/v2.47.1/prometheus-2.47.1.linux-amd64.tar.gz
```

### 3️⃣ Extract and Move Prometheus Files
```sh
tar -xvf prometheus-2.47.1.linux-amd64.tar.gz
cd prometheus-2.47.1.linux-amd64/
sudo mkdir -p /data /etc/prometheus
sudo mv prometheus promtool /usr/local/bin/
sudo mv consoles/ console_libraries/ /etc/prometheus/
sudo mv prometheus.yml /etc/prometheus/prometheus.yml
```

### 4️⃣ Set Directory Permissions
```sh
sudo chown -R prometheus:prometheus /etc/prometheus/ /data/
```

## ⚙️ Configuring Prometheus as a System Service

### 1️⃣ Create a Systemd Service File
Open the Prometheus service file:
```sh
sudo vim /etc/systemd/system/prometheus.service
```

### 2️⃣ Add the Following Configuration:
```ini
[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=prometheus
Group=prometheus
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/prometheus \
  --config.file=/etc/prometheus/prometheus.yml \
  --storage.tsdb.path=/data \
  --web.console.templates=/etc/prometheus/consoles \
  --web.console.libraries=/etc/prometheus/console_libraries \
  --web.listen-address=0.0.0.0:9090 \
  --web.enable-lifecycle

[Install]
WantedBy=multi-user.target
```

### 3️⃣ Enable and Start Prometheus
```sh
sudo systemctl enable prometheus
sudo systemctl start prometheus
```

### 4️⃣ Verify Prometheus Status
```sh
sudo systemctl status prometheus
```

## 🌍 Accessing Prometheus Web Interface
Open your browser and navigate to:
```
http://<your-server-ip>:9090
```

Prometheus is now up and running! 🚀
