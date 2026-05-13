# Troubleshooting — UptimeMonitoring

## Dashboard not reachable locally

```bash
docker compose ps
docker compose logs --tail=100 uptime-kuma
```

Open:

```text
http://localhost:3001
```

The compose file binds the dashboard to localhost for safety.

## Cloudflare URL not reachable

Check route target:

```text
http://uptime-kuma:3001
```

Check tunnel logs:

```bash
docker compose logs --tail=100 tunnel
```

## Telegram notification fails

- Confirm the bot token is correct.
- Send a message to the bot before using Auto Get.
- Test notification from Uptime Kuma settings.

## False positive alerts

If HTTP monitor fails because of TLS/redirect issues, use TCP Port monitor for internal services.

## Container data missing after restart

Check that `./uptime-kuma-data:/app/data` exists and is mounted correctly.
