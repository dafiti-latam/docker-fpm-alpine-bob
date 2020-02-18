FROM dftlatam/docker-fpm-alpine-bob:onbuild

RUN apk add --no-cache git \
    && apk del rabbitmq-c-dev libressl-dev \
    && apk add --no-cache --virtual .build-deps autoconf bash build-base pcre-dev openssl-dev \
    && cd /tmp \
    && git clone \
        --branch v1.2.0 \
        --depth 1 \
        https://github.com/edenhill/librdkafka.git \
    && cd librdkafka \
    && ./configure \
    && make \
    && make install \
    && pecl install rdkafka-3.1.2 \
    && docker-php-ext-enable rdkafka \
    && rm -rf /tmp/librdkafka \
    && apk del .build-deps \
    && apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/main/ --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ --allow-untrusted libressl-dev rabbitmq-c-dev
