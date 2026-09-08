# Speedtest Tracker

Scheduled speed tests backed by a local SQLite database. The production database, TLS key,
logs, and generated Nginx/PHP configuration are excluded.

Generate a unique application key, for example with `openssl rand -base64 32`, and place it
after the `base64:` prefix in your local `.env`. Keep the dashboard private unless you have
reviewed the information it exposes.
