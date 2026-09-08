# Grafana Alloy

Collects Docker logs and host metrics, then forwards them to Loki and a Prometheus remote
write endpoint. Create the external `monitoring` network, copy `.env.example` to `.env`,
and enter your own endpoints and credentials.

The Docker socket exposes sensitive host metadata even when mounted read-only. Keep the
Alloy HTTP interface bound to loopback unless remote access is explicitly required.
