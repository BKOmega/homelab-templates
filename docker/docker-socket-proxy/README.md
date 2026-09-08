# Docker socket proxy

Read-mostly HTTP proxy for selected Docker API endpoints. It consolidates several
host-specific deployments into one reusable template and denies mutating operations by
default.

The proxy still exposes sensitive Docker metadata and runs privileged. Do not expose port
2375 to an untrusted network. Prefer leaving it on the external `docker-api` network and
remove the host port when only containers need access.
