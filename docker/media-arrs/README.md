# Media automation

VPN-routed Prowlarr, Sonarr, Radarr, qBittorrent, SABnzbd, FlareSolverr, Notifiarr,
Unpackerr, and Swaparr. All application containers share Gluetun's
network namespace, matching the source architecture without publishing production media,
application databases, backups, API keys, VPN credentials, or host paths.

Review the VPN provider's Gluetun requirements and replace every secret placeholder. Ports
are loopback-bound by default. `SWAPARR_DRY_RUN` starts as `true`; confirm its behaviour
before allowing it to remove downloads. The `/dev/net/tun` device and `NET_ADMIN` capability
are security-sensitive and required for the VPN tunnel.
