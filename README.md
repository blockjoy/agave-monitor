
# Solana Monitor

This project monitors Solana/Agave validator metrics. 

## Prerequisites

- **Git**: To clone the repository
- **Python**: To run the application

## Start the application

### 1. Clone the Repository
Download the project source code:
```bash
git clone https://github.com/calebcall/solana-monitor-public /root/solana-monitor-public/
cd /root/solana-monitor-public
```

### 2. Create venv and install dependencies
python3 -m venv monitor-env
monitor-env/bin/pip install -r requirements.txt

### 3. Configure config.yml
```bash
/root/solana-monitor-public/config.yml
```

### 4. Move service file in to place and enable service
```bash
cp /root/solana-monitor-public/agave-monitor.service /etc/systemd/system/
systemctl daemon-reload
systemctl enable agave-monitor
```

### 5. Start Service
```bash
systemctl start agave-monitor
```

### Node Exporter Metrics

To monitor system-level metrics such as CPU, memory, and disk usage, you can use the **Node Exporter**.

You can download and import the Node Exporter dashboard with **ID 1860** from Grafana's dashboard library:

1. Go to Grafana and navigate to **Dashboards** > **Import**.
2. Enter the **Dashboard ID: `1860`** and click **Load**.
3. Select your Prometheus datasource and click **Import**.

This will provide a comprehensive overview of your system's performance using Node Exporter metrics.

--- 

### Credit
Orignal work from [qskyhigh](https://github.com/qskyhigh/solana-monitor-public)<br>

If you found this project helpful, feel free to support by donating SOL to qskyhigh's wallet.

**SOL Wallet Address**: `FNu9BCwCmgSmeCa56LCAErPBNeAdgnQJsBrrLgVbbMKt`

<img src="https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png" alt="Buy Me A Coffee">