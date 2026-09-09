# Authentik

Authentik server and worker with PostgreSQL and Redis. Runtime databases, media, generated
certificates, and private templates are deliberately excluded.

Create the external proxy network, copy `.env.example` to `.env`, generate a unique
`AUTHENTIK_SECRET_KEY` and database password, then validate and start the stack.

The worker mounts the Docker socket to manage embedded outposts. That grants extensive host
control; remove the mount if you do not use Docker-managed outposts.

## How I use this pattern

Authentik is the application-facing identity broker in a wider identity design. Directory
identity remains separate from application protocol translation: applications that support
modern SSO consume OIDC or SAML through Authentik, while other services can retain direct
directory or local authentication where that is the better fit.

The Docker deployment therefore represents the Authentik application tier rather than the
complete identity authority. Docker-managed outposts are supported where useful, but the
socket access required by the worker is treated as a privileged capability.

## Why this differs from the upstream example

The Compose structure remains intentionally close to a conventional Authentik deployment.
The HomeLab-specific value is its role in the wider identity architecture and the deliberate
distinction between directory authority, browser SSO and break-glass/local access.

Related: [Identity with FreeIPA and Authentik](https://www.bitsandbytes.co.uk/designs/identity-freeipa-authentik/)
