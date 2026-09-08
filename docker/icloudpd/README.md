# iCloud Photos Downloader

One primary downloader plus optional `hidden` and `shared` profiles. Production Apple IDs,
passwords, library identifiers, photo libraries, and authentication cookies are excluded.
This version uses the web UI password and MFA providers instead of putting an iCloud
password in `.env`.

```bash
docker network create photos
cp .env.example .env
docker compose up -d
docker compose --profile hidden --profile shared up -d
```

Complete authentication through the loopback-bound web UI. The cookie volume contains
authentication material; back it up and protect it as a credential store.
