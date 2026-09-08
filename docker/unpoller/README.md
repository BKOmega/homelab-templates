# Unpoller

Collects UniFi metrics and writes them to InfluxDB. The private `up.conf`, controller URL,
site inventory, and credentials have been replaced with environment variables.

Use a dedicated read-only UniFi account where possible and an InfluxDB token scoped only
to the target bucket. Keep both credentials in the local `.env`.
