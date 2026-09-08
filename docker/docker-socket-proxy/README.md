# Docker socket proxy

Read-only HTTP proxy for selected Docker API endpoints. Its default surface permits
container discovery plus Docker API ping and version negotiation. Events, images, system
information, networks, services, tasks, and volumes remain disabled unless explicitly
enabled for a trusted consumer in `.env`.

The proxy is not privileged, uses a read-only filesystem, and explicitly denies archive,
filesystem-change, export, log, process-list, and mutation operations. It has no published
host port and joins the external `docker-api` network for trusted cross-stack consumers.

Docker API proxy traffic is unauthenticated. Membership of `docker-api` grants every member
the visibility enabled here, so use a dedicated network and never attach general application
containers to it. Prefer a separate narrowly configured proxy and private network where a
consumer can be isolated within one stack.
