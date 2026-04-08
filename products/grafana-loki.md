# Grafana + Loki + Prometheus

**Category:** Logging, Monitoring & Alerting
**Type:** Self-hosted
**Jurisdiction:** EU-hostable; Grafana Labs is US-based but the software is open source and fully self-hostable
**Website:** [grafana.com](https://grafana.com)

## What It Is

The standard observability stack for self-hosted infrastructure:

| Component | Role |
|---|---|
| **Prometheus** | Metrics collection and storage (CPU, memory, request rates, etc.) |
| **Loki** | Log aggregation — like Prometheus but for logs |
| **Grafana** | Dashboards and visualization for both metrics and logs |
| **Promtail** | Log shipper: tails log files and sends them to Loki |
| **Alertmanager** | Routes alerts from Prometheus to email, Slack (Mattermost), etc. |

Together these replace Datadog, Splunk, and PaperTrail with zero data leaving your EU server.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run the full observability stack on your own EU-owned infrastructure |

## Architecture

```
[Your Apps / Servers]
        │
        ├─── Prometheus scrapes ──→ Prometheus (metrics store)
        │                                    │
        └─── Promtail ships logs ──→ Loki (log store)
                                             │
                                     Grafana (dashboards)
                                             │
                                     Alertmanager (alerts)
```

## Setup (Docker Compose)

### Directory Structure

```
observability/
├── docker-compose.yml
├── prometheus/
│   └── prometheus.yml
├── loki/
│   └── loki-config.yml
├── promtail/
│   └── promtail-config.yml
└── alertmanager/
    └── alertmanager.yml
```

### docker-compose.yml

```yaml
version: "3"

networks:
  monitoring:

volumes:
  prometheus_data:
  loki_data:
  grafana_data:

services:
  prometheus:
    image: prom/prometheus:latest
    restart: unless-stopped
    volumes:
      - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus
    command:
      - "--config.file=/etc/prometheus/prometheus.yml"
      - "--storage.tsdb.retention.time=90d"
    ports:
      - "9090:9090"
    networks:
      - monitoring

  loki:
    image: grafana/loki:latest
    restart: unless-stopped
    volumes:
      - ./loki/loki-config.yml:/etc/loki/loki-config.yml
      - loki_data:/loki
    command: -config.file=/etc/loki/loki-config.yml
    ports:
      - "3100:3100"
    networks:
      - monitoring

  promtail:
    image: grafana/promtail:latest
    restart: unless-stopped
    volumes:
      - ./promtail/promtail-config.yml:/etc/promtail/promtail-config.yml
      - /var/log:/var/log:ro
      - /var/lib/docker/containers:/var/lib/docker/containers:ro
    command: -config.file=/etc/promtail/promtail-config.yml
    networks:
      - monitoring

  alertmanager:
    image: prom/alertmanager:latest
    restart: unless-stopped
    volumes:
      - ./alertmanager/alertmanager.yml:/etc/alertmanager/alertmanager.yml
    ports:
      - "9093:9093"
    networks:
      - monitoring

  grafana:
    image: grafana/grafana:latest
    restart: unless-stopped
    volumes:
      - grafana_data:/var/lib/grafana
    environment:
      GF_SECURITY_ADMIN_USER: admin
      GF_SECURITY_ADMIN_PASSWORD: changeme
      GF_SERVER_DOMAIN: grafana.your-company.eu
      GF_SERVER_ROOT_URL: https://grafana.your-company.eu
      GF_ANALYTICS_REPORTING_ENABLED: "false"
      GF_ANALYTICS_CHECK_FOR_UPDATES: "false"
    ports:
      - "3000:3000"
    networks:
      - monitoring
```

### prometheus/prometheus.yml

```yaml
global:
  scrape_interval: 15s
  evaluation_interval: 15s

alerting:
  alertmanagers:
    - static_configs:
        - targets: ["alertmanager:9093"]

rule_files:
  - "/etc/prometheus/rules/*.yml"

scrape_configs:
  - job_name: prometheus
    static_configs:
      - targets: ["localhost:9090"]

  # Scrape Node Exporter on each server
  - job_name: node
    static_configs:
      - targets:
          - "your-server-1:9100"
          - "your-server-2:9100"

  # Scrape Docker containers via cAdvisor
  - job_name: cadvisor
    static_configs:
      - targets: ["cadvisor:8080"]
```

### loki/loki-config.yml

```yaml
auth_enabled: false

server:
  http_listen_port: 3100

ingester:
  lifecycler:
    address: 127.0.0.1
    ring:
      kvstore:
        store: inmemory
      replication_factor: 1
  chunk_idle_period: 1h
  max_chunk_age: 1h

schema_config:
  configs:
    - from: 2024-01-01
      store: boltdb-shipper
      object_store: filesystem
      schema: v11
      index:
        prefix: index_
        period: 24h

storage_config:
  boltdb_shipper:
    active_index_directory: /loki/boltdb-shipper-active
    cache_location: /loki/boltdb-shipper-cache
    shared_store: filesystem
  filesystem:
    directory: /loki/chunks

limits_config:
  retention_period: 90d

compactor:
  working_directory: /loki/compactor
  shared_store: filesystem
  retention_enabled: true
```

### promtail/promtail-config.yml

```yaml
server:
  http_listen_port: 9080

positions:
  filename: /tmp/positions.yaml

clients:
  - url: http://loki:3100/loki/api/v1/push

scrape_configs:
  # Collect all Docker container logs
  - job_name: docker
    docker_sd_configs:
      - host: unix:///var/run/docker.sock
        refresh_interval: 5s
    relabel_configs:
      - source_labels: [__meta_docker_container_name]
        target_label: container

  # Collect system logs
  - job_name: system
    static_configs:
      - targets: [localhost]
        labels:
          job: varlogs
          __path__: /var/log/*.log
```

### alertmanager/alertmanager.yml

```yaml
route:
  group_by: ["alertname"]
  group_wait: 30s
  group_interval: 5m
  repeat_interval: 3h
  receiver: mattermost

receivers:
  - name: mattermost
    webhook_configs:
      - url: "https://chat.your-company.eu/hooks/your-webhook-id"
        send_resolved: true
```

## Adding Node Exporter (Per Server)

Run this on every server you want to monitor:

```yaml
# On the target server
services:
  node-exporter:
    image: prom/node-exporter:latest
    restart: unless-stopped
    network_mode: host
    pid: host
    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro
    command:
      - "--path.procfs=/host/proc"
      - "--path.sysfs=/host/sys"
      - "--path.rootfs=/rootfs"
```

## Grafana Setup

1. Open `https://grafana.your-company.eu`
2. Log in with admin credentials
3. **Connections** → **Data Sources** → **Add**:
   - Add **Prometheus**: URL `http://prometheus:9090`
   - Add **Loki**: URL `http://loki:3100`
4. **Dashboards** → **Import** → use these community dashboard IDs:
   - `1860` — Node Exporter Full (server metrics)
   - `893` — Docker and system monitoring
   - `12611` — Loki logs overview
   - `15141` — Docker container logs

## nginx Reverse Proxy

```nginx
server {
    listen 443 ssl;
    server_name grafana.your-company.eu;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto https;
    }
}
```

## Querying Logs (LogQL)

```logql
# All logs from the "nextcloud" container
{container="nextcloud"}

# Error logs from the last hour
{container="mattermost"} |= "error"

# Count error rate per minute
sum(rate({job="docker"} |= "error" [1m])) by (container)

# Filter by log level
{container="app"} | json | level="error"
```

## Key Features

- Real-time log streaming and search
- 90-day log retention (configurable)
- Metrics dashboards (CPU, memory, disk, network per container/server)
- Alerting via Mattermost/email/webhook
- Log correlation with metrics (click a spike → see logs at that time)
- No data sent externally

## Compliance Notes

- Fully self-hosted: all logs and metrics stay on your EU servers
- Grafana telemetry disabled via `GF_ANALYTICS_REPORTING_ENABLED: "false"`
- Prometheus and Loki have no external reporting
- Logs may contain personal data — configure retention and access control accordingly (GDPR Art. 5)
- Restrict Grafana access to internal network or VPN

## Alternatives Considered

| Alternative | Why not |
|---|---|
| Datadog | US company, logs leave EU |
| Splunk | US company, expensive, data leaves EU |
| New Relic | US company |
| PaperTrail | US company (SolarWinds) |
