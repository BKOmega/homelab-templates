# Caddy

Custom Caddy build with RFC 2136 DNS and CrowdSec modules. The supplied Caddyfile is a
single internal-CA reverse-proxy example; it deliberately replaces the production site
inventory, certificates, trust stores, OCSP cache, and private upstream map.

Set the example site, upstream, and CrowdSec values in `.env`. The RFC 2136 variables are
provided for users who replace `tls internal` with an RFC 2136 DNS challenge. The admin API
listens only on the container's loopback interface and is not published by Compose. Run
`docker compose exec caddy caddy reload --config /etc/caddy/Caddyfile` to reload from inside
the container. Protect the CrowdSec API key.
