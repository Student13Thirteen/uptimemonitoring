# 🛠️ Uptime Kuma Setup & Configuration Guide

This guide explains how to deploy Uptime Kuma via Docker on a local Linux server, expose it securely via Cloudflare Tunnel, and set up local service monitoring with Telegram notifications.

## 📋 Prerequisites
- A Linux server with Docker installed (e.g., `192.168.1.10`).
- A Cloudflare Zero Trust account.
- The Telegram app.

---

## Step 1: Docker Installation
Deploying Uptime Kuma takes just a single Docker command.

1. SSH into your server.
2. Create a persistent data directory:
   ```bash
   mkdir -p ~/uptime-kuma
   ```
3. Run the Docker container in the background with auto-restart enabled:
   ```bash
   sudo docker run -d --restart=unless-stopped -p 3001:3001 -v ~/uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1
   ```
4. Access the web interface locally at `http://192.168.1.10:3001` and create your admin account.

---

## Step 2: Secure Remote Access (Cloudflare Tunnel)
To access the dashboard from anywhere without a VPN:

1. Go to your **Cloudflare Zero Trust** dashboard.
2. Navigate to **Networks** -> **Tunnels** -> Select your tunnel -> **Configure**.
3. Under the **Public Hostname** tab, click **Add a public hostname**.
4. Fill in the details:
   - **Subdomain:** `status` (or your preferred name)
   - **Domain:** Select your domain (e.g., `example.com`)
   - **Service Type:** `HTTP`
   - **URL:** `192.168.1.10:3001` (or `localhost:3001`)
5. Save. You can now securely manage Uptime Kuma at `https://status.example.com`.

---

## Step 3: Telegram Notifications Setup
Uptime Kuma sends outbound requests to Telegram, so no static IP or port forwarding is required.

1. Open Telegram and search for `@BotFather`.
2. Start a chat and send `/newbot`.
3. Choose a name and a username (must end in `bot`).
4. Copy the **Bot Token** provided by BotFather.
5. Click the link to your new bot and send it a random message (e.g., "Hello"). *This is required to initiate the chat!*
6. In the Uptime Kuma dashboard, go to **Settings** -> **Notifications** -> **Setup Notification**.
7. Select **Telegram** as the type.
8. Paste your **Bot Token**.
9. Click the **Auto Get** button next to the Chat ID field (Kuma will read your "Hello" message and fetch the ID automatically).
10. Click **Test**, then **Save**.

---

## Step 4: Adding Local Monitors (TCP Port Method)
When monitoring services hosted on the same server/network (like Nextcloud or PocketBase), using standard `HTTP/s` monitoring can sometimes cause `SSL wrong version number` errors due to internal HTTPS redirects. 
The most reliable way to monitor local containers is by checking their **TCP Port**.

1. Click **Add New Monitor**.
2. **Monitor Type:** Select `TCP Port`.
3. **Friendly Name:** `Nextcloud` (or service name).
4. **Hostname:** `192.168.1.10` (Your server's local IP).
5. **Port:** `8080` (The internal port of the service).
6. **Heartbeat Interval:** `300` (Every 5 minutes to save resources).
7. Select your Telegram notification on the right side and click **Save**.

---

## 🔧 Troubleshooting: SSH Disconnections
*Issue:* After setting up monitoring, your SSH session to the server might drop frequently due to the constant network polling interfering with Keep-Alive mechanisms.

*Fix:* Configure your server's SSH daemon to actively keep the connection alive.
1. Edit the SSH config file:
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
2. Add these two lines at the bottom (or uncomment and edit them):
   ```text
   ClientAliveInterval 15
   ClientAliveCountMax 120
   ```
3. Save the file and restart the SSH service:
   ```bash
   sudo systemctl restart ssh
   ```
This forces the server to send an invisible ping every 15 seconds, completely preventing idle timeouts!
