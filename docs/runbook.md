# Runbook — UptimeMonitoring

## Daily check

```bash
docker compose ps
docker compose logs --tail=80 uptime-kuma
docker compose logs --tail=80 tunnel
```

## When an alert arrives

1. Identify affected service.
2. Check whether only public endpoint is down or local service is down too.
3. SSH into server.
4. Run `docker compose ps` in the affected project.
5. Check logs.
6. Restart only the affected service if safe.
7. Confirm recovery in Uptime Kuma.
8. Write a short incident note.

## Backup Uptime Kuma data

```bash
docker compose stop uptime-kuma
tar -czf backup_uptime_kuma_$(date +%Y%m%d_%H%M).tar.gz uptime-kuma-data
docker compose start uptime-kuma
```
