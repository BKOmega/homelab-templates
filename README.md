# HomeLab Templates

Reusable, sanitised infrastructure templates derived from applications running in a
working home lab. This repository is a curated set of examples, not a backup of the
production environment. Production credentials, private addressing, private domains,
runtime data, certificates, and host-specific topology are not included.

## Using a Docker template

1. Choose a directory under `docker/`.
2. Read its `README.md`, including any security or external-network requirements.
3. Copy `.env.example` to `.env` and replace every `<CHANGE_ME>` or similar placeholder.
4. Review bind mounts, published ports, and image tags for your environment.
5. Validate with `docker compose config`.
6. Start it with `docker compose up -d` only after completing the application-specific setup.

Real `.env` files are ignored by Git. Never commit credentials or private key material.

## Available Docker templates

| Template | Purpose |
| --- | --- |
| [Alloy](docker/alloy/) | Host metrics and Docker log collection |
| [Arcane agent](docker/arcane-agent/) | Remote Arcane Docker agent |
| [Arcane manager](docker/arcane-manager/) | Arcane management service |
| [Authentik](docker/authentik/) | Identity provider with PostgreSQL and Redis |
| [Authentik proxy](docker/authentik-proxy/) | Remote Authentik proxy outpost |
| [Caddy](docker/caddy/) | Internal reverse proxy with DNS and CrowdSec modules |
| [cAdvisor](docker/cadvisor/) | Container resource metrics |
| [Cloudflare DDNS](docker/cloudflare-ddns/) | Cloudflare DNS record updater |
| [CrowdSec](docker/crowdsec/) | Central CrowdSec Local API and log processor |
| [CrowdSec agent](docker/crowdsec-agent/) | Remote log processor using a central Local API |
| [Diode](docker/diode/) | NetBox Labs Diode services |
| [Docker socket proxy](docker/docker-socket-proxy/) | Restricted HTTP proxy for the Docker socket |
| [Grafana](docker/grafana/) | Metrics and log dashboards with optional OIDC |
| [Homepage](docker/homepage/) | Application dashboard with safe example configuration |
| [iCloud Photos Downloader](docker/icloudpd/) | iCloud photo download service |
| [IT-Tools](docker/it-tools/) | Browser-based IT utilities |
| [Komodo](docker/komodo/) | Komodo core, database, and local periphery |
| [Komodo periphery](docker/komodo-periphery/) | Remote Komodo periphery agent |
| [Media automation](docker/media-arrs/) | VPN-routed media automation applications |
| [Media support](docker/media-support/) | Media request, maintenance, and exporter services |
| [Orb agent](docker/orb/) | NetBox Labs network discovery agent |
| [Prometheus](docker/prometheus/) | Metrics collection server |
| [Speedtest Tracker](docker/speedtest-tracker/) | Scheduled internet speed tests |
| [Squid](docker/squid/) | Authenticated forward proxy |
| [Traefik](docker/traefik/) | Edge reverse proxy with ACME DNS validation |
| [TrueCommand](docker/truecommand/) | TrueNAS management service |
| [Unpoller](docker/unpoller/) | UniFi metrics collector |
| [Uptime Kuma](docker/uptime-kuma/) | Availability monitoring |
| [Watchtower](docker/watchtower/) | Label-scoped container updates |
| [What's Up Docker](docker/whats-up-docker/) | Container image update monitoring |

Templates intentionally use example domains and documentation-only addresses. Values
such as `10.10.10.10`, `192.0.2.10`, and `service.example.internal` are illustrative.
