FROM dftlatam/docker-fpm-alpine:5.6

RUN set -xe \
  && apk add --no-cache wget git autoconf gcc g++ make \
  && pecl install xdebug-2.5.5 \
  && wget https://getcomposer.org/composer.phar \
  && mv composer.phar /usr/local/bin/composer \
  && chmod 755 /usr/local/bin/composer \
  && apk del wget git autoconf gcc g++ make
