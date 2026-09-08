# Squid

Authenticated forward-proxy template. It intentionally excludes the production password
file, logs, cache, TLS certificates, and TLS interception rules.

Create a local credential file before starting the container:

```bash
mkdir -p secrets
htpasswd -c secrets/passwords proxy-user
cp .env.example .env
docker compose config
docker compose up -d
```

`secrets/passwords` is ignored by Git. Keep the proxy bound to loopback or a trusted
network and restrict access with a host firewall.
