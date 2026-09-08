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
