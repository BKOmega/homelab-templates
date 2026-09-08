# Komodo periphery

Remote Komodo periphery agent. Set the same passkey used by Komodo core and restrict
`PERIPHERY_ALLOWED_IPS` to the core server. The default bind address is loopback; choose a
trusted management address when the core runs on another host.

This container has broad host access through the Docker socket, `/proc`, and an unconfined
AppArmor profile. Use TLS for traffic crossing an untrusted network and protect the agent
port with host firewall rules.
