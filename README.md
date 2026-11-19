# Forge — Sovereign Git Version Control & Native Docker CI/CD

Forge is a self-hosted, sovereign Git version control system and CI/CD platform offering complete independence from foreign SaaS clouds, zero seat licensing costs, and complete code privacy.

---

## Architecture Overview

```
                      ┌──────────────────────────────────────┐
                      │  forge.linuxguy.space (Nginx Ingress)│
                      └──────────────────┬───────────────────┘
                                         │
                 ┌───────────────────────┴───────────────────────┐
                 │                                               │
      (Unauthenticated /)                             (Authenticated /)
                 ▼                                               ▼
    ┌───────────────────────────┐                 ┌───────────────────────────┐
    │ Forge Static Landing Page │                 │   Gitea Instance (:3000)  │
    │ - Three.js Molten Celestial│                │ - Sovereign Git Engine    │
    │ - Interactive Terminal    │                 │ - Pull Requests & Issues  │
    │ - Comparison Matrix       │                 │ - User Profiles & Projects│
    └───────────────────────────┘                 └─────────────┬─────────────┘
                                                                │
                                                  ┌─────────────┴─────────────┐
                                                  ▼                           ▼
                                      ┌───────────────────────┐   ┌───────────────────────┐
                                      │   Gitea Act Runner    │   │     Docker Socket     │
                                      │   (forge-runner)      │   │  (Native Docker CI)   │
                                      └───────────────────────┘   └───────────────────────┘
```

---

## Core Capabilities

- **Airgapped Code Privacy**: 100% self-hosted on bare-metal NVMe. Zero telemetry, zero AI training on private repositories.
- **Native Docker CI/CD**: Gitea Actions with local Docker runner executing GitHub Actions compatible workflows (`.forge/workflows/*.yaml` or `.github/workflows/*.yaml`).
- **Intelligent Ingress Routing**:
  - Automatically serves the modern sovereign marketing landing page to unauthenticated visitors.
  - Automatically passes authenticated users straight to their Gitea Dashboard (`/`) without landing page friction.
- **Git Smart HTTP & SSH**: High-speed cloning, pushing, LFS tracking, and commit hooks.
- **Turnstile & Rate-Limiting Defense**: Integrated bot protection on authentication endpoints.

---

## Quickstart

### Prerequisites
- Docker & Docker Compose
- Nginx reverse proxy

### Run with Docker Compose
```bash
# Clone or navigate to directory
cd /home/debian/forge

# Start Gitea and Act Runner
docker compose up -d
```

### Services
- **Gitea Service**: `forge-gitea` running on `127.0.0.1:3000`
- **Actions Runner**: `forge-runner` executing workflows inside isolated containers

---

## License
MIT License. Sovereign, self-hosted, telemetry-free.
