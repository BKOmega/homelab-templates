# Caddy

Custom Caddy build with RFC 2136 DNS and CrowdSec modules. The supplied Caddyfile is a
single internal-CA reverse-proxy example; it deliberately replaces the production site
inventory, certificates, trust stores, OCSP cache, and private upstream map.

Set the example site, upstream, and CrowdSec values in `.env`. The RFC 2136 variables are
provided for users who replace `tls internal` with an RFC 2136 DNS challenge. The admin API
listens only on the container's loopback interface and is not published by Compose. Run
`docker compose exec caddy caddy reload --config /etc/caddy/Caddyfile` to reload from inside
the container. Protect the CrowdSec API key.

## How I use this pattern

Caddy is the internal reverse-proxy tier in my HomeLab. It handles services that do not
need an internet-facing entry point and is intentionally separate from the external
Traefik path.

The deployed configuration contains many private upstreams and certificate details, so the
public template reduces that inventory to a single representative service while retaining
the useful pattern: internal TLS, CrowdSec integration and support for RFC 2136 DNS where
DNS-based certificate automation is appropriate.

## Why this differs from the upstream example

This is not simply a stock Caddy container. It uses a custom build to add the DNS and
CrowdSec modules required by the wider HomeLab design, and it keeps the Caddy administrative
API inside the container rather than publishing a management endpoint.

Related: [Two reverse proxies, two trust boundaries](https://www.bitsandbytes.co.uk/designs/two-proxy-trust-boundaries/)
