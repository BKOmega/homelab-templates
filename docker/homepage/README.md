# Homepage

Homepage with a minimal, generic dashboard and a restricted Docker socket proxy. The
production service inventory, private URLs, hostnames, widget credentials, custom icons,
logs, and personal dashboard content are not included.

Create the external dashboard network, copy `.env.example` to `.env`, and edit the YAML in
`config/`. Keep widget API keys in local environment variables or another secret mechanism;
never write them directly into tracked YAML.

The socket proxy is privileged. It is reachable only on the dashboard network and allows a
small read-only API subset.
