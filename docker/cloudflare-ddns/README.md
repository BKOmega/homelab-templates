# Cloudflare DDNS

Updates selected Cloudflare DNS records from the host's detected public address. Create a
narrowly scoped API token that can edit only the required DNS zone, set `DOMAINS`, and keep
the local `.env` private.

The service uses host networking but drops Linux capabilities, runs read-only, and enables
`no-new-privileges`.
