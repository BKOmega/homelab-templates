# CrowdSec

Central CrowdSec Local API and log processor. The generated hub cache, database, console
enrolment, bouncer files, and production acquisition inventory are excluded. Adjust
`config/acquis.yaml` and the read-only host paths for your own logs.

Generate a unique bouncer key and keep the Local API bound to a trusted address. The
example exposes metrics and the Local API on loopback by default.

## How I use this pattern

CrowdSec is distributed across the HomeLab rather than treated as a security feature owned
by one reverse proxy. A central Local API provides the shared decision point, while agents
or proxy-local components process the logs available at their respective trust boundaries.

This lets edge and internal services participate in the same broader security model
without requiring the public template to expose the production log inventory, machine
identities or bouncer credentials.

## Why this differs from the upstream example

The useful part of these templates is the central-LAPI/distributed-agent relationship. They
are intended to show how separate Docker hosts or proxy tiers can contribute to one
CrowdSec design rather than demonstrating a single all-in-one container.

Related: [Security telemetry, analysis, and response](https://www.bitsandbytes.co.uk/designs/security-telemetry-and-response/)
