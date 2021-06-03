
# build

FROM rust:1.42.0-alpine3.11 as builder 

RUN apk update \
    && apk add --no-cache \
        ca-certificates \
        build-base \
        linux-headers \
        git \
        openssl-dev \
        util-linux-dev \
        libseccomp-dev \
    && mkdir -p /usr/src/app \
    && cd /usr/src/app \
    && git clone https://github.com/lskatz/fasten \
    && cd /usr/src/app/fasten \
    && cargo build --release


# build final container

FROM alpine:3.11

COPY --from=builder /usr/src/app/fasten/target/release /usr/local/bin

