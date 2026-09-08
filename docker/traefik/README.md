# Traefik

Edge reverse proxy with a restricted Docker socket sidecar, Cloudflare DNS-01 ACME, a
loopback-bound dashboard, a dynamic security-header policy, and a test `whoami` router.

Create the external proxy network, copy `.env.example` to `.env`, enter a narrowly scoped
Cloudflare token, and replace the example hostname. Runtime ACME state and logs are ignored
by Git. The token must be able to edit only the required DNS zone.

The Docker API sidecar is privileged and should never be reachable outside the proxy
network. The dashboard uses Traefik's insecure listener but is loopback-bound by default;
do not publish it without adding authentication.
