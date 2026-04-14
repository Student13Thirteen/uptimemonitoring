# 🐻 Uptime Kuma - Homelab Monitoring

![Uptime Kuma](https://img.shields.io/badge/Uptime_Kuma-1.x-brightgreen?style=for-the-badge&logo=uptime-kuma)
![Docker](https://img.shields.io/badge/Docker-Ready-blue?style=for-the-badge&logo=docker)
![Cloudflare](https://img.shields.io/badge/Cloudflare-Zero_Trust-orange?style=for-the-badge&logo=cloudflare)

This repository contains the documentation and setup instructions for the central monitoring system of my homelab. 
The system is built on **[Uptime Kuma](https://github.com/louislam/uptime-kuma)**, providing real-time uptime tracking and instant Telegram alerts for all my self-hosted services (like Nextcloud and PocketBase).

## 🌟 Features
- **24/7 Monitoring**: Checks the health of internal Docker containers every 5 minutes.
- **Telegram Alerts**: Instant push notifications to a smartphone when a service goes down or recovers.
- **Secure Remote Access**: Exposed to the web securely via a Cloudflare Zero Trust Tunnel without opening any router ports.
- **Bypass SSL Issues**: Uses TCP Port monitoring to check container health natively, avoiding internal SSL/HTTPS redirect loops.

## 📚 Documentation
Check out the complete step-by-step setup guide here:
👉 **[Setup & Configuration Guide](setup_uptimekuma.md)**

---
*Part of my Homelab Infrastructure.*
