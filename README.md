
# Solana Monitor

This project monitors Solana/Agave validator metrics. 

## Prerequisites

- **Git**: To clone the repository
- **Python**: To run the application
- **Metrics Collector**: To scrape the service `/metrics` endpoint
- **Logs Collector**: To scrape the logs from the validator and monitor

## Start the application

### 1. Clone the Repository
Download the project source code:
```bash
git clone https://github.com/blockjoy/agave-monitor.git /root/agave-monitor/
cd /root/agave-monitor
```

### 2. Create venv and install dependencies
python3 -m venv monitor-env
monitor-env/bin/pip install -r requirements.txt

### 3. Configure config.yml
```bash
/root/agave-monitor/config.yml
```

### 4. Move service file in to place and enable service
```bash
cp /root/agave-monitor/agave-monitor.service /etc/systemd/system/
systemctl daemon-reload
systemctl enable agave-monitor
```

### 5. Start Service
```bash
systemctl start agave-monitor
```

### 6. Configure metrics and logs collectors
Any prometheus compatible collector will work.  Some examples:
  - [Alloy](https://grafana.com/docs/alloy/latest/ "From Grafana") (metrics and logs)
  - [Vector](https://vector.dev "From Datadog") (metrics and logs)
  - [Node Exporter](https://github.com/prometheus/node_exporter "From the prometheus project") (metrics only)
  - [Promtail](https://grafana.com/docs/loki/latest/send-data/promtail/installation/) (logs only)
  
1. Configure metrics to scrape the port configured in `config.yml` and endpoint `/metrics`<br>
  (e.g. `http://localhost:12344/metrics`)
2. Configure logs collection<br>
  - Location of validator logs
  - Location of monitor process logs (default: `logs/monitor.log`)
  
---

### Grafana Dashboard
The dashboard can be imported from the docs/ directory to your Grafana instance<br>
  - Default is to utilize a label applied by the collector `job: agave` (can be editted to match your environment)

### Node Exporter Metrics

To monitor system-level metrics such as CPU, memory, and disk usage, you can use the **Node Exporter**.

You can download and import the Node Exporter dashboard with **ID 1860** from Grafana's dashboard library:

1. Go to Grafana and navigate to **Dashboards** > **Import**.
2. Enter the **Dashboard ID: `1860`** and click **Load**.
3. Select your Prometheus datasource and click **Import**.

This will provide a comprehensive overview of your system's performance using Node Exporter metrics.
