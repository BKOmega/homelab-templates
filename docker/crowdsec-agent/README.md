# CrowdSec agent

Remote CrowdSec log processor connected to a central Local API. Register the machine on
the central instance, place its generated machine username and password in `.env`, and
adjust `config/acquis.yaml` for the logs available on this host.

No Local API database, bouncer key, downloaded hub cache, or production log inventory is
included.

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
