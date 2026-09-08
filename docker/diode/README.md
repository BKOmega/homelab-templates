# Diode

NetBox Labs Diode ingress, ingester, reconciler, Redis, PostgreSQL, Hydra, and authentication
services. This is reconstructed from the deployed topology without its databases, OAuth
credentials, private NetBox endpoint, or runtime state.

Before deployment:

1. Copy `.env.example` to `.env` and replace all secret placeholders.
2. Copy `config/oauth2/client-credentials.json.example` to
   `config/oauth2/client-credentials.json` and replace every placeholder.
3. Create the external `application` network.
4. Run `docker compose config` and review the Hydra issuer and NetBox URL.

The real credential JSON is ignored by Git. Hydra runs with `--dev`, matching the source
architecture; do not expose it or the Diode ingress to an untrusted network without a
production Hydra configuration and TLS. Database init scripts run only on an empty volume.
