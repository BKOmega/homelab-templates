# Homepage

Homepage with a minimal, generic dashboard and a restricted Docker socket proxy. The
production service inventory, private URLs, hostnames, widget credentials, custom icons,
logs, and personal dashboard content are not included.

Create the external dashboard network, copy `.env.example` to `.env`, and edit the YAML in
`config/`. Keep widget API keys in local environment variables or another secret mechanism;
never write them directly into tracked YAML.

The LinuxServer socket proxy is not privileged, uses a read-only filesystem, and allows
only container discovery plus Docker API ping and version negotiation. Archive, export,
logs, process listing, filesystem changes, and all mutations are explicitly denied.

Homepage and the proxy share a private internal `docker-api` network. Only Homepage joins
the external `dashboard` network; the proxy has no host port and is not reachable by other
dashboard applications. Access to the proxy still grants the configured Docker metadata
visibility, so do not attach additional containers to `docker-api`.

## How I use this pattern

Homepage provides a convenient application view, but I do not want a dashboard container
to receive unrestricted Docker socket access simply so it can discover running services.

The template therefore places Homepage and a restricted Docker API proxy on a stack-private
network. Homepage can also join the normal dashboard/application network, but other
containers on that network cannot reach the Docker proxy.

The production dashboard contains private service names, URLs, widgets and credentials, so
the public YAML deliberately shows only a small representative inventory.

## Why this differs from the upstream example

The main difference is Docker discovery isolation. The dashboard does not mount the Docker
socket directly and the socket proxy allows only the small read-only API surface required
for container discovery.
