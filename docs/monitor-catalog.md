# Monitor Catalog

Suggested monitors for the related portfolio projects.

## DockNextFlare / Nextcloud

| Field | Value |
|---|---|
| Type | TCP Port or HTTP(s) |
| Hostname | server local IP or public hostname |
| Port | `8080` if local debug port exists, otherwise public HTTPS check |
| Interval | 300 seconds |

## PwaTruckPocket / PocketBase

| Field | Value |
|---|---|
| Type | TCP Port or HTTP(s) |
| Hostname | server local IP or public hostname |
| Port | `8090` if bound locally |
| Interval | 300 seconds |

## Cloudflare public endpoints

Use HTTP(s) monitor against the public URL to verify user-facing availability.

## Notes

- TCP checks answer “is the service port reachable?”
- HTTP checks answer “is the application endpoint responding correctly?”
- Use both when possible for critical services.
