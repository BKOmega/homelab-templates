# Komodo periphery

Remote Komodo periphery agent. Set the same passkey used by Komodo core and restrict
`PERIPHERY_ALLOWED_IPS` to the core server. The default bind address is loopback; choose a
trusted management address when the core runs on another host.

This container has broad host access through the Docker socket, `/proc`, and an unconfined
AppArmor profile. Use TLS for traffic crossing an untrusted network and protect the agent
port with host firewall rules.

## How I use this pattern

Komodo follows a central-management and distributed-agent model. A core instance provides
the management plane while Periphery components provide controlled access to Docker hosts.

That makes network placement and agent trust more important than simply exposing the
Komodo web interface. Periphery requires substantial host visibility, so its allowed-source
controls and management-network placement should be treated as part of the security model.

## Why this differs from the upstream example

The templates retain both the local and remote management patterns instead of publishing
only the central application. They also make the host-level trust granted to Periphery
explicit rather than presenting it as an ordinary application container.
