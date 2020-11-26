FROM mswebmaster/php:7.3-cli-alpine
MAINTAINER MsWebmaster

ENV COMPOSER_CACHE_DIR=/cache

RUN apk add --update openssh git curl && \
    curl -k -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=1.10.16 && \
    apk del curl && \
    rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/local/bin/composer"]
