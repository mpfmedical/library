# syntax=docker/dockerfile:latest

FROM golang:alpine AS builder

RUN <<EOF
go install github.com/caddyserver/xcaddy/cmd/xcaddy@latest
xcaddy build \
    --output /go/bin/caddy \
    --with github.com/baldinof/caddy-supervisor
EOF

FROM alpine:latest

COPY --from=builder /go/bin/caddy /usr/bin/caddy

ENTRYPOINT [ "/usr/bin/caddy" ]
