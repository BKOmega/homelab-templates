# Watchtower

Label-scoped container update monitoring with a loopback-bound HTTP API. Add
`com.centurylinklabs.watchtower.enable=true` only to containers you explicitly want it to
manage.

The Docker socket grants host control. Generate a unique HTTP API token and leave API
updates disabled unless you require and protect them. Notification URLs often contain
credentials and must remain in the local `.env`.
