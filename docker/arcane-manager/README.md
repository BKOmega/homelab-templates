# Arcane manager

Runs the Arcane manager with local application, build, and backup directories. Create the
external management network before deployment:

```bash
docker network create management
cp .env.example .env
docker compose config
docker compose up -d
```

Generate unique high-entropy values for `ENCRYPTION_KEY` and `JWT_SECRET`. OIDC is optional.
The Docker socket gives this container effectively root-level control of the host; deploy
only trusted images and do not expose the service directly to untrusted networks.

## How I use this pattern

Arcane is another example of a management service where the important boundary is the
Docker host rather than the web UI alone. The manager provides the central application
while agents extend management to additional Docker hosts.

The deployment is therefore kept on a trusted management path, with optional OIDC for the
user-facing service and explicit recognition that Docker socket access effectively grants
host-level container control.

## Why this differs from the upstream example

The public templates retain the manager/agent separation and management-network assumptions
from the working HomeLab rather than collapsing everything into a single-host demonstration.
