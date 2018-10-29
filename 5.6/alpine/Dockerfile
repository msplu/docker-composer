FROM mswebmaster/php:5.6-cli-alpine

ENV COMPOSER_CACHE_DIR=/cache

RUN apk add --update openssh git curl && \
    curl -k -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    apk del curl && \
    rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/local/bin/composer"]

