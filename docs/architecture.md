# Architecture — UptimeMonitoring

## Goal

Provide a central monitoring dashboard for self-hosted services and send alerts when services go down or recover.

## Components

| Component | Role |
|---|---|
| Uptime Kuma | Monitoring dashboard and health-check scheduler |
| Telegram | Notification channel |
| Cloudflare Tunnel | Secure dashboard access without public router ports |
| Docker volume | Persistent Uptime Kuma data |

## Alert flow

```text
Uptime Kuma monitor check
        │
        ├── OK → no action
        │
        └── DOWN → Telegram alert → operator checks runbook/logs
```

## Monitoring strategy

- Use TCP Port checks for internal services when HTTP/TLS redirects create false positives.
- Use HTTP checks for public endpoints where full application availability matters.
- Use conservative intervals for homelab resources, for example every 300 seconds.
