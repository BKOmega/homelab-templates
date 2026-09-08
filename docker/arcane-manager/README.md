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
