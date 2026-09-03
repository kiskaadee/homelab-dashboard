# 📊 Homelab Dashboard (getHomepage + Learning Hub)

Unified personal portal for the homelab infrastructure, combining:
1. **getHomepage**: Service catalog, dynamic system widgets, and bookmark launcher.
2. **Learning API (FastAPI + Turso)**: Backend service powering the embedded interactive Kanban board in the dashboard UI.

Part of the [homelab-core](https://github.com/kiskaadee/homelab-core) cluster ecosystem.

---

## 🏗️ Architecture & Stack

- **Dashboard**: `ghcr.io/gethomepage/homepage:latest` (Port `3000`)
- **Learning Backend**: Custom Python/FastAPI app in `./learning/` (Port `8000`)
- **Database**: Cloud Turso / LibSQL
- **Ingress**: Traefik (attached to `proxy-net` & `socket-net`)

---

## ⚙️ Environment Variables & Secrets

Decrypted globally from SOPS via `/run/secrets/rendered/traefik-deployments.env`:

| Variable | Description | Default / Example |
| :--- | :--- | :--- |
| `SERVICE_DOMAIN` | Dashboard FQDN | `dashboard.arch-services.mywire.org` |
| `LEARNING_DOMAIN` | Learning Backend API FQDN | `learning.arch-services.mywire.org` |
| `TURSO_DATABASE_URL` | Turso connection string | Loaded from SOPS |
| `TURSO_AUTH_TOKEN` | Turso authentication token | Loaded from SOPS |
| `PROXY_NETWORK` | Docker gateway network | `proxy-net` |

---

## 🚀 Deployment

### Via Orchestrator (`appctl`)
```bash
appctl up homelab-dashboard
appctl logs homelab-dashboard
```

### Manual Deployment
```bash
docker compose up --build -d
```
