# Authentik proxy outpost

Remote proxy-outpost template. Create an outpost in Authentik, place its generated token in
your local `.env`, and connect the container to the same Docker network as the applications
it protects. Never commit the outpost token.
