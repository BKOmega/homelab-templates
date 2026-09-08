# Prometheus

Prometheus with a self-scrape and one documentation-only node-exporter target. Replace the
example target with your own service discovery or scrape configuration. The production
target inventory, database, WAL, and host mappings are excluded.

The lifecycle endpoint is enabled for controlled configuration reloads. Keep the web port
on a trusted address or place it behind authentication.
