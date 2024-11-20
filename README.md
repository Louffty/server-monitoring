
# Server Monitoring with Docker: Prometheus, Grafana, and Node Exporter  

This project provides a Dockerized setup for monitoring server metrics using **Prometheus**, **Grafana**, and **Node Exporter**. It enables a comprehensive view of your server’s health, resource utilization, and performance through customizable dashboards.

---

## Features  
- **Prometheus**: Collects and stores time-series data.  
- **Node Exporter**: Exposes hardware and OS metrics for Prometheus.  
- **Grafana**: Visualizes the collected data in dynamic dashboards.

---

## Prerequisites  
- Docker and Docker Compose installed on your server.  
- Basic knowledge of Docker and Prometheus configurations.  

---

## Deployment Instructions  

### 1. Clone the Repository  
```bash  
git clone https://github.com/Louffty/server-monitoring.git
cd server-monitoring  
```  

### 2. Configure Prometheus  
The configuration file `prometheus.yml` is already included in the repository. It sets up:  
- A scrape interval of 15 seconds.  
- Prometheus and Node Exporter as scrape targets.  

If needed, you can adjust the `prometheus.yml` file to fit your requirements.

### 3. Start the Services  
Run the following command to start Prometheus, Grafana, and Node Exporter using Docker Compose:  
```bash  
docker compose up -d  
```  

### 4. Access the Applications  

- **Prometheus**: Visit [http://your-server-ip:9090](http://your-server-ip:9090)  
- **Grafana**: Visit [http://your-server-ip:3000](http://your-server-ip:3000)  
  - Default credentials:  
    - Username: `admin`  
    - Password: `admin`  

### 5. Import the Node Exporter Dashboard  

Grafana offers a pre-configured dashboard for monitoring Node Exporter metrics. To import it:  
1. Log in to Grafana.  
2. Go to **Dashboards > Import**.  
3. In the **Import via grafana.com** field, enter the dashboard ID `1860`.  
4. Click **Load**.  
5. Set the Prometheus data source and click **Import**.  

You can now view the detailed metrics collected by Node Exporter in an interactive and visually rich format.

---

## Customization  

### Modify Prometheus Configuration  
To add more scrape targets or jobs, edit `prometheus.yml` and restart the services:  
```bash  
docker compose down  
docker compose up -d  
```  

### Persist Grafana Data  
Grafana data is stored in the `grafana_data` Docker volume, ensuring your configurations and dashboards persist across container restarts.

---

## Monitoring Metrics  
With the imported dashboard, you can monitor:  
- CPU and memory usage.  
- Disk I/O and storage.  
- Network activity.  
- System load and uptime.  

---

## Troubleshooting  

### Check Logs  
Use the following commands to view logs for each service:  
- Prometheus: `docker logs prometheus`  
- Grafana: `docker logs grafana`  
- Node Exporter: `docker logs node_exporter`  

### Restart Services  
If any service fails, restart it:  
```bash  
docker compose restart <service-name>  
```  

---

With this setup, you’ll have a fully operational monitoring system for your servers.
