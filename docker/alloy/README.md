# Grafana Alloy

Collects Docker logs and host metrics, then forwards them to Loki and a Prometheus remote
write endpoint. Create the external `monitoring` network, copy `.env.example` to `.env`,
and enter your own endpoints and credentials.

The Docker socket exposes sensitive host metadata even when mounted read-only. Keep the
Alloy HTTP interface bound to loopback unless remote access is explicitly required.

## How I use this pattern

Alloy is used as a collection layer rather than as the final monitoring destination. It
can collect container logs and host-level metrics close to the Docker host and forward them
to central observability services.

That fits the wider HomeLab approach of separating signal collection from storage,
dashboards and alerting rather than expecting one monitoring product to answer every
operational question.

## Why this differs from the upstream example

The template combines two useful collection paths in one agent: Docker log discovery for
Loki and host metrics for Prometheus remote write. The destinations and credentials are
parameterised, but that dual-purpose edge-collection role is retained.

Related: [Observability in layers](https://www.bitsandbytes.co.uk/designs/observability-layers/)
