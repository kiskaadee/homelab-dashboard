# 📊 Homelab Dashboard (getHomepage)

Standalone personal navigation dashboard and application launcher for the homelab infrastructure.

Part of the [homelab-core](https://github.com/kiskaadee/homelab-core) cluster ecosystem.

---

## 🏗️ Architecture & Requirements

- **Compositor / Proxy**: Traefik (attached to `proxy-net` & `socket-net`)
- **Domain**: `dashboard.arch-services.mywire.org` (or `dashboard.roadtotech.me`)
- **Container Image**: `ghcr.io/gethomepage/homepage:latest`

---

## ⚙️ Environment Variables & Configuration

| Variable | Description | Default / Example |
| :--- | :--- | :--- |
| `SERVICE_DOMAIN` | FQDN routed by Traefik | `dashboard.arch-services.mywire.org` |
| `PROXY_NETWORK` | External Docker network | `proxy-net` |

---

## 🚀 Deployment

### Via Orchestrator (`appctl`)
```bash
appctl up dashboard
appctl logs dashboard
```

### Manual Deployment
```bash
docker compose up -d
```
