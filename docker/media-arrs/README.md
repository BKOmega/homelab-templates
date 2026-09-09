# Media automation

VPN-routed Prowlarr, Sonarr, Radarr, qBittorrent, SABnzbd, FlareSolverr, Notifiarr,
Unpackerr, and Swaparr. All application containers share Gluetun's
network namespace, matching the source architecture without publishing production media,
application databases, backups, API keys, VPN credentials, or host paths.

Review the VPN provider's Gluetun requirements and replace every secret placeholder. Ports
are loopback-bound by default. `SWAPARR_DRY_RUN` starts as `true`; confirm its behaviour
before allowing it to remove downloads. The `/dev/net/tun` device and `NET_ADMIN` capability
are security-sensitive and required for the VPN tunnel.

## How I use this pattern

The media automation services are treated as one networked application group rather than a
collection of unrelated containers. Applications that need the VPN path share Gluetun's
network namespace, so their outbound connectivity and published management ports are
controlled through that common boundary.

Storage and application state remain outside the public template. The important reusable
part is the relationship between the services and the shared VPN path.

## Why this differs from the upstream example

Individual Sonarr, Radarr, Prowlarr, qBittorrent and SABnzbd examples are easy to find
upstream. This template is useful because it demonstrates how those applications are
composed together around Gluetun, including supporting automation such as Unpackerr and
Swaparr.
