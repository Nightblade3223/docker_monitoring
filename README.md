# 📊 Full Observability Stack

This repository provides a Docker Compose-based observability stack to monitor metrics, logs, and containers across Docker, Proxmox, network devices, and NAS systems. It includes **Prometheus**, **Grafana**, **Loki**, **Promtail**, **cAdvisor**, and **Node Exporter**.

---

## 🔧 Included Services

### 1. **Prometheus**

* **Purpose**: Collects and stores time-series metrics.
* **Exposed Port**: `9090`
* **Config Location**: `./prometheus/prometheus.yml`
* **Usage**: Scrapes exporters like `node_exporter`, `cadvisor`, `snmp_exporter`, and custom app metrics.

---

### 2. **Grafana**

* **Purpose**: Visualizes metrics and logs from Prometheus and Loki.
* **Exposed Port**: `3000`
* **Default Login**: `admin / admin`
* **Usage**: Import dashboards or build your own to monitor system health, containers, and infrastructure.

---

### 3. **Loki**

* **Purpose**: Aggregates and indexes logs.
* **Exposed Port**: `3100`
* **Usage**: Lightweight logging backend designed to work seamlessly with Grafana.

---

### 4. **Promtail**

* **Purpose**: Forwards host logs to Loki.
* **Volumes**:

  * `/var/log`: Reads system logs.
  * `./promtail/config.yml`: Defines log targets and labels.
* **Usage**: Attach labels to logs (e.g., job, hostname) and send them to Loki for storage and visualization.

---

### 5. **cAdvisor**

* **Purpose**: Monitors container resource usage and performance.
* **Exposed Port**: `8080`
* **Usage**: Prometheus scrapes container metrics through this exporter.

---

### 6. **Node Exporter**

* **Purpose**: Collects system-level metrics (CPU, memory, disk, etc.).
* **Exposed Port**: `9100`
* **Usage**: Essential for monitoring host system performance in Prometheus.

---

## 🚀 Getting Started

1. **Clone the repo**

   ```bash
   git clone https://github.com/your-org/observability-stack.git
   cd observability-stack
   ```

2. **Create configuration folders**

   ```bash
   mkdir -p prometheus grafana loki promtail
   ```

3. **Start the stack**

   ```bash
   docker compose up -d
   ```

4. **Access Interfaces**:

   * Grafana: [http://localhost:3000](http://localhost:3000)
   * Prometheus: [http://localhost:9090](http://localhost:9090)
   * cAdvisor: [http://localhost:8080](http://localhost:8080)

---

## 📈 Extend the Stack

* **Proxmox Monitoring**: Add [Proxmox Exporter](https://github.com/prometheus-pve/prometheus-pve-exporter)
* **NAS/Network Monitoring**: Use `snmp_exporter` and configure SNMP on devices
* **Tracing Support**: Add [Grafana Tempo](https://grafana.com/oss/tempo/)

---

## 📂 Folder Structure

```bash
.
├── docker-compose.yml
├── prometheus/
│   └── prometheus.yml
├── loki/
│   └── config.yml
├── promtail/
│   └── config.yml
└── grafana/
```

---

## 📜 License

MIT License

---

## 🧑‍💻 Maintainer

**Your Name** – [@yourhandle](https://github.com/yourhandle)
