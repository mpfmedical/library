# syntax=docker/dockerfile:latest

FROM golang:alpine3.19 AS builder

RUN <<EOF
go install github.com/caddyserver/xcaddy/cmd/xcaddy@latest
xcaddy build \
    --output /go/bin/caddy \
    --with github.com/baldinof/caddy-supervisor
EOF

FROM alpine:3.19

COPY --from=builder /go/bin/caddy /usr/bin/caddy

ENTRYPOINT [ "/usr/bin/caddy" ]
