# Traefik

Edge reverse proxy with a restricted Docker socket sidecar, Cloudflare DNS-01 ACME, a
dynamic security-header policy, and a test `whoami` router.

Create the external proxy network, copy `.env.example` to `.env`, enter a narrowly scoped
Cloudflare token, and replace the example hostname. Runtime ACME state and logs are ignored
by Git. The token must be able to edit only the required DNS zone.

The Docker API sidecar is attached only to the internal `docker-api` network shared with
Traefik; proxied applications join only the external `proxy` network. The sidecar is
read-only, is not privileged, and explicitly denies filesystem export, archive, change,
log, process-list, and mutation routes. Treat access to it as equivalent to privileged
Docker metadata access.

Traefik's insecure API listener is disabled and port 8080 is not published. To expose the
dashboard, add an explicit HTTPS router for `api@internal` with authentication and an
appropriate source allowlist.
