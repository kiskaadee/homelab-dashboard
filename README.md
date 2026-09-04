# 📊 Homelab Dashboard (Homepage & Learning Hub)

Unified service dashboard portal and learning hub backend for the `roadtotech.me` homelab cluster.

---

## 🏗️ Architecture & Requirements

- **Proxy Network**: Attached to external `proxy-net`
- **Socket Network**: Attached to `socket-net` for container discovery
- **Domain**: `dashboard.roadtotech.me`
- **Learning Hub API**: `learning.roadtotech.me`
- **Target Ports**: `3000` (Homepage UI), `8000` (FastAPI / SQLite backend)

---

## ⚙️ Configuration & Metadata (`app.yaml`)

This application is self-describing via `app.yaml`:

```yaml
name: "dashboard"
aliases:
  - "dash"
domain: "dashboard.roadtotech.me"
description: "Homelab Service Dashboard & Application Launcher"
visible: false
auth: false
networks:
  - proxy-net
  - socket-net
env:
  LEARNING_DOMAIN: "learning.roadtotech.me"
```

Homepage's `config/services.yaml` is dynamically generated from all registered `Sites/*/app.yaml` manifests using `appctl sync`.

---

## 🚀 Deployment

### Via Orchestrator (`appctl`)
```bash
appctl up dashboard
# or using the shortcut alias
appctl up dash
```

### Manual Deployment
```bash
docker compose up -d
```

---

## 📄 License
This repository is released into the public domain under the [Unlicense](LICENSE).
