# Komodo

Komodo core with MongoDB and a local periphery agent. Create the external management
network, copy `.env.example` to `.env`, and replace all secret placeholders before use.

```bash
docker network create management
cp .env.example .env
docker compose config
docker compose up -d
```

The periphery service mounts the Docker socket and `/proc` and disables the AppArmor
profile, giving it extensive host access. Restrict `PERIPHERY_ALLOWED_IPS`, keep Komodo on
a trusted management network, and enable TLS when communicating across untrusted networks.

## How I use this pattern

Komodo follows a central-management and distributed-agent model. A core instance provides
the management plane while Periphery components provide controlled access to Docker hosts.

That makes network placement and agent trust more important than simply exposing the
Komodo web interface. Periphery requires substantial host visibility, so its allowed-source
controls and management-network placement should be treated as part of the security model.

## Why this differs from the upstream example

The templates retain both the local and remote management patterns instead of publishing
only the central application. They also make the host-level trust granted to Periphery
explicit rather than presenting it as an ordinary application container.
