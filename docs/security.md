# Security Notes — UptimeMonitoring

## Secrets

Never commit:

```text
.env
Cloudflare tunnel token
Uptime Kuma backup archives
```

## Dashboard exposure

The compose file binds Uptime Kuma to localhost:

```yaml
ports:
  - "127.0.0.1:3001:3001"
```

Remote access should go through Cloudflare Tunnel.

## Access control

- Use a strong admin password.
- Protect Cloudflare account with MFA.
- Avoid sharing public dashboard links broadly.
