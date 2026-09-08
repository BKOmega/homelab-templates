# Orb agent

NetBox Labs Orb with generic network and SNMPv3 discovery examples. The production subnet
map, device inventory, site metadata, SNMP credentials, and Diode client credentials are
replaced with documentation addresses and environment variables.

Review every target in `config/agent.yaml` before starting. The agent uses host networking,
runs privileged, and adds `NET_RAW` and `NET_ADMIN`; those permissions are required for
broad discovery but expose the host. Run it only on an appropriately isolated scanner.
