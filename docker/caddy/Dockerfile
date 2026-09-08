FROM caddy:2-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/rfc2136@latest \
    --with github.com/caddyserver/transform-encoder \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http@latest \
    --with github.com/hslatman/caddy-crowdsec-bouncer/layer4@latest \
    --with github.com/hslatman/caddy-crowdsec-bouncer/appsec@latest

FROM caddy:2
COPY --from=builder /usr/bin/caddy /usr/bin/caddy
