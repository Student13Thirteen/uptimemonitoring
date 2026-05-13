# UptimeMonitoring — Homelab Service Monitoring

Central monitoring setup for self-hosted services using **Uptime Kuma**, Docker and Telegram alerts.  
The goal is to monitor internal services such as Nextcloud and PocketBase and receive fast notifications when something goes down or recovers.

> Portfolio focus: service reliability, monitoring, alerting, incident awareness and operational runbook thinking.

## What this project demonstrates

- Docker-based monitoring deployment
- Service health checks for self-hosted infrastructure
- Telegram alerting for downtime/recovery events
- Cloudflare Tunnel access without router port forwarding
- Operational documentation and troubleshooting workflows

## Architecture

```text
Uptime Kuma container
   │
   ├── TCP/HTTP checks → Nextcloud, PocketBase, internal services
   │
   ├── Telegram notifications → phone / operations chat
   │
   └── Cloudflare Tunnel → secure remote dashboard access
```

## Repository structure

```text
uptimemonitoring/
├── cloudflared/
│   └── config.yml.example
├── docs/
│   ├── architecture.md
│   ├── deployment.md
│   ├── monitor-catalog.md
│   ├── runbook.md
│   ├── troubleshooting.md
│   └── screenshots/
├── .env.example
├── docker-compose.yml
├── LICENSE
└── README.md
```

## Quick start

```bash
git clone https://github.com/Student13Thirteen/uptimemonitoring.git
cd uptimemonitoring
cp .env.example .env
nano .env
docker compose up -d
```

Open locally:

```text
http://localhost:3001
```

Then create the first admin user and configure Telegram notifications.

## Documentation

| Document | Purpose |
|---|---|
| [`docs/architecture.md`](docs/architecture.md) | Monitoring architecture and alert flow |
| [`docs/deployment.md`](docs/deployment.md) | Step-by-step deployment |
| [`docs/monitor-catalog.md`](docs/monitor-catalog.md) | Suggested monitors for your services |
| [`docs/runbook.md`](docs/runbook.md) | Operational checks and incident handling |
| [`docs/troubleshooting.md`](docs/troubleshooting.md) | Common issues and fixes |

## Useful commands

```bash
# Check containers
docker compose ps

# View logs
docker compose logs -f

# Restart Uptime Kuma
docker compose restart uptime-kuma

# Stop stack
docker compose down
```

## License

MIT — see [`LICENSE`](LICENSE).
