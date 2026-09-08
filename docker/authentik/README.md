# Authentik

Authentik server and worker with PostgreSQL and Redis. Runtime databases, media, generated
certificates, and private templates are deliberately excluded.

Create the external proxy network, copy `.env.example` to `.env`, generate a unique
`AUTHENTIK_SECRET_KEY` and database password, then validate and start the stack.

The worker mounts the Docker socket to manage embedded outposts. That grants extensive host
control; remove the mount if you do not use Docker-managed outposts.
