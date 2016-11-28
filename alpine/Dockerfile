FROM php:7.1-rc-alpine

ENV COMPOSER_CACHE_DIR=/cache

COPY config/php.ini /usr/local/etc/php/

RUN apk add --update openssh git curl freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev libmcrypt-dev && \
    docker-php-ext-configure gd \
        --with-gd \
        --with-freetype-dir=/usr/include/ \
        --with-png-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ && \
    NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    docker-php-ext-install -j${NPROC} gd mcrypt && \
    curl -k -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    apk del curl freetype-dev libpng-dev libjpeg-turbo-dev && \
    rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/local/bin/composer"]
