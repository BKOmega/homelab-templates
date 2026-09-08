# CrowdSec agent

Remote CrowdSec log processor connected to a central Local API. Register the machine on
the central instance, place its generated machine username and password in `.env`, and
adjust `config/acquis.yaml` for the logs available on this host.

No Local API database, bouncer key, downloaded hub cache, or production log inventory is
included.
