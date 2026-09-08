# CrowdSec

Central CrowdSec Local API and log processor. The generated hub cache, database, console
enrolment, bouncer files, and production acquisition inventory are excluded. Adjust
`config/acquis.yaml` and the read-only host paths for your own logs.

Generate a unique bouncer key and keep the Local API bound to a trusted address. The
example exposes metrics and the Local API on loopback by default.
