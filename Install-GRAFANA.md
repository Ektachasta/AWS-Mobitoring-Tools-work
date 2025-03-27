# 📊 Install and Configure Grafana on Ubuntu 22.04

## 📖 Overview
Grafana is a powerful open-source platform for monitoring and observability, providing stunning dashboards and visualizations. This guide walks you through installing Grafana on **Ubuntu 22.04** and integrating it with **Prometheus** for real-time monitoring.

---

## 🚀 Installation Steps

### 1️⃣ Install Dependencies
Ensure all necessary dependencies are installed:
```sh
sudo apt-get update
sudo apt-get install -y apt-transport-https software-properties-common
```

### 2️⃣ Add the Grafana GPG Key
To verify package authenticity, add the official Grafana GPG key:
```sh
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```

### 3️⃣ Add the Grafana Repository
Add the **Grafana OSS (Open Source Software) repository**:
```sh
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

### 4️⃣ Install Grafana
Update the package list and install Grafana:
```sh
sudo apt-get update
sudo apt-get -y install grafana
```

### 5️⃣ Enable and Start the Grafana Service
Enable Grafana to start on boot:
```sh
sudo systemctl enable grafana-server
```
Start the Grafana service:
```sh
sudo systemctl start grafana-server
```

### 6️⃣ Check Grafana Status
Ensure Grafana is running correctly:
```sh
sudo systemctl status grafana-server
```

---

## 🌍 Access Grafana Web Interface
Once Grafana is running, open your web browser and navigate to:
```
http://<your-server-ip>:3000
```
- **Default Credentials:**
  - **Username:** `admin`
  - **Password:** `admin`
- On first login, you will be prompted to change the password for security reasons.

---

## 🔗 Integrate Prometheus with Grafana
### 1️⃣ Add Prometheus as a Data Source
1. Click on the **gear icon (⚙️) → Configuration** in the sidebar.
2. Select **Data Sources**.
3. Click **Add data source**.
4. Choose **Prometheus**.
5. Set the **URL** to:
   ```
   http://localhost:9090
   ```
6. Click **Save & Test** to confirm the connection.

### 2️⃣ Import a Pre-Configured Dashboard
1. Click the **+ (plus icon) → Dashboard**.
2. Select **Import**.
3. Enter a pre-made dashboard ID (e.g., `1860` for Prometheus metrics).
4. Click **Load**.
5. Select **Prometheus** as the data source.
6. Click **Import** to visualize metrics.

---

## 🎨 Customizing Grafana
Grafana allows you to:
✅ Create custom dashboards 📊  
✅ Set up alerts 🚨  
✅ Connect multiple data sources 🌍  

Explore its full potential and customize it to fit your monitoring needs!

---

## 🎉 Congratulations!
You have successfully installed **Grafana** and connected it with **Prometheus**. Now, you can create stunning dashboards to monitor your infrastructure in real-time! 🚀
