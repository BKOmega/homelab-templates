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

## How I use this pattern

In my HomeLab, Traefik is the external reverse-proxy tier rather than the proxy for every
application. Public traffic reaches this tier through the perimeter, while internal-only
applications use a separate proxy path.

The design deliberately limits what Traefik can discover and what networks it can reach.
Docker metadata comes through a constrained socket proxy on a private network, while
proxied applications join a separate application-facing proxy network. Certificate
issuance uses DNS-01 so validation does not depend on exposing an additional HTTP challenge
path.

The public template keeps that architecture while replacing the production hostnames,
routes and backend inventory with representative values.

## Why this differs from the upstream example

The important difference is the trust boundary rather than the Traefik syntax. This
template does not mount the Docker socket directly, does not enable the insecure dashboard
listener, uses explicit opt-in discovery and separates Docker API access from application
proxy traffic.

Related: [Two reverse proxies, two trust boundaries](https://www.bitsandbytes.co.uk/designs/two-proxy-trust-boundaries/)
· [Traefik ACME diagnostics](https://www.bitsandbytes.co.uk/runbooks/traefik-acme-diagnostics/)
