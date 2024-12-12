# Grafana Loki Prometheus (English Version)

## Project Overview

This project focuses on implementing monitoring and logging using **Grafana**, **Loki**, and **Prometheus**. It provides efficient solutions for data visualization and logging, enabling real-time monitoring of application status.

This project is developed based on and inspired by the [grafana-prometheus-rdbms](https://github.com/solo5star/grafana-prometheus-rdbms) source.

---

## Key Features

1. **Grafana Dashboard**

   - Real-time data visualization
   - Customizable widgets and charts
   - Integration with various data sources

2. **Logging with Loki**

   - Aggregated logging in distributed environments
   - Fast and simple log queries

3. **Metric Collection with Prometheus**

   - Collects metrics from applications and servers
   - Configurable alerts and notification system

4. **Exporter Integration**

   - **mysqld\_exporter**: Collects MySQL database metrics
   - **node\_exporter**: Collects server and system metrics
   - **promtail**: Collects and forwards logs to Loki

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

Below is an example configuration file for Prometheus using **mysqld\_exporter**, **node\_exporter**, and **promtail**:

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

