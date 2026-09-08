# Media support

Seerr, Maintainerr, Calibre, Profilarr, Tautulli, and Prometheus exporters for Sonarr,
Radarr, Prowlarr, and SABnzbd. Production libraries, application state, plugins, user data,
API keys, and private service URLs are excluded.

Every port is loopback-bound by default. Replace exporter URLs and API-key placeholders,
and review local storage ownership. Calibre keeps the source deployment's unconfined seccomp
profile; this weakens isolation and should be removed if your installation works without it.
