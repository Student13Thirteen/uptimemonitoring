# Deployment Guide — UptimeMonitoring

## 1. Environment

```bash
cp .env.example .env
nano .env
```

Set:

```env
CLOUDFLARE_TOKEN=
```

## 2. Cloudflare config

```bash
mkdir -p cloudflared
cp cloudflared/config.yml.example cloudflared/config.yml
nano cloudflared/config.yml
```

Route public hostname to:

```text
http://uptime-kuma:3001
```

## 3. Start stack

```bash
docker compose up -d
docker compose ps
```

## 4. First login

Open:

```text
http://localhost:3001
```

or your Cloudflare public hostname, then create the admin account.

## 5. Telegram notification

1. Create a bot with `@BotFather`.
2. Send a message to the bot.
3. In Uptime Kuma: Settings → Notifications → Telegram.
4. Paste the token and use Auto Get for Chat ID.
5. Test and save.
