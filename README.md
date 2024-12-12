# Grafana Loki Prometheus

## Project Overview
This project focuses on implementing monitoring and logging using **Grafana**, **Loki**, and **Prometheus**. It provides efficient solutions for data visualization and logging, enabling real-time monitoring of application status.

---

## Key Features

1. **Grafana Dashboard**
   - Real-time data visualization
   - Customizable widgets and charts
   - Supports integration with various data sources

2. **Logging with Loki**
   - Aggregates logs in distributed environments
   - Simple and fast log queries

3. **Metric Collection with Prometheus**
   - Collects metrics from applications and servers
   - Configurable alerts and notifications

4. **Exporter Integration**
   - **mysqld_exporter**: Collects MySQL database metrics
   - **node_exporter**: Collects server and system metrics
   - **promtail**: Integrates with Loki for log collection and forwarding

---

## Tech Stack

- **Backend:** Prometheus, Loki
- **Frontend:** Grafana
- **Containerization:** Docker, Docker Compose
- **Languages:** YAML (for configuration)

---

## Installation and Usage

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Heesunni/grafana_loki_prometheus.git
   cd grafana_loki_prometheus
   ```

2. **Run Docker Compose**
   ```bash
   docker-compose up -d
   ```

3. **Access Grafana**
   - Open your browser and go to `http://localhost:3000`
   - Default login credentials:
     - Username: `admin`
     - Password: `admin`

4. **Set Up Prometheus and Loki**
   - Prometheus: `http://localhost:9090`
   - Loki: Add log sources and configure Grafana as a data source

---

## Folder Structure

```
├── docker-compose.yml       # Docker Compose configuration file
├── grafana/                 # Grafana configurations and data
├── prometheus/              # Prometheus configuration files
├── loki/                    # Loki configuration files
└── README.md                # Project documentation
```

---

## Use Cases

- Application performance monitoring
- Log analysis and debugging
- Setting up system alerts and notifications

---

## Prometheus Configuration Example

Below is an example configuration file for Prometheus using **mysqld_exporter**, **node_exporter**, and **promtail**:

```yaml
# prometheus.yml

global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']

  - job_name: 'mysqld_exporter'
    static_configs:
      - targets: ['localhost:9104']

  - job_name: 'promtail'
    static_configs:
      - targets: ['localhost:9080']
```

This configuration assumes the exporters are running on localhost. Modify the IP addresses or ports as needed.





