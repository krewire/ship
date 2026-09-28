# ship

**ship** is the Krewire ecosystem's zero-cost infrastructure orchestrator and deployment automation engine.

## Overview

ship powers containerless, zero-downtime application deployments across raw virtual machines, systemd-managed services, and cloud environments:

- **Target Adapters** — Flexible targets (`binary`, `gh-pages`, `systemd`, `infra`)
- **Zero-Downtime Releases** — Atomic symlink switching and graceful drain
- **Automated TLS & Reverse Proxy** — Provisioning for native Go services
- **Multi-Environment Pipelines** — Staging and production release automation

## Usage

```bash
# Deploy website to GitHub Pages
kiw deploy --target gh-pages

# Deploy binary service to target server
kiw deploy --target binary --env prod

# Provision zero-cost cloud / VM infrastructure
kiw deploy --target infra --env prod --plan
```

## Architecture

Part of the Krewire unified framework vision ([KWF-M8K2Q](https://github.com/krewire/framework/blob/main/docs/specs/KWF-ARCH-M8K2Q-unified-framework-vision.md) and [KWF-B7N3D](https://github.com/krewire/framework/blob/main/docs/specs/KWF-INFRA-B7N3D-infra-target-deploy.md)).