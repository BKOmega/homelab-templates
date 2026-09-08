# Grafana

Grafana with persistent local data and optional generic OIDC. The production database,
plugins, CA certificate, LDAP file, dashboards, and login credentials are not included.

Set unique admin and secret-key values. If OIDC is disabled, the placeholder OIDC values
are not used; remove them from your local `.env` if preferred. Ensure the data directory is
writable by the configured UID and GID.
