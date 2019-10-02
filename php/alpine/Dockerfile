FROM php:fpm-alpine

LABEL maintainer="emin şen"
LABEL maintainer.author="contact@emnsen.com"

ENV COMPOSER_ALLOW_SUPERUSER=1

ADD composer.sh /root/

RUN apk --no-cache --virtual .build-deps add \
  gcc make g++ zlib-dev autoconf \
  libpng-dev icu-dev dpkg-dev \
  libxml2-dev libxslt-dev libbz2 libzip-dev bzip2-dev libevent-dev \
  libjpeg-turbo-dev zlib-dev freetype-dev zeromq-dev rabbitmq-c-dev \
  && apk --no-cache add \
  libbz2 libzmq libzip libxml2 libxslt libpng libjpeg \
  libpq libevent libmemcached libmemcached-libs rabbitmq-c \
  openssl icu curl git supervisor freetype mysql-client openssh-client \
  && docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-png-dir=/usr/include/ --with-jpeg-dir=/usr/include \
  && docker-php-ext-install bcmath bz2 calendar exif gd intl pdo pdo_mysql mysqli opcache soap sockets pcntl xsl \
  && docker-php-ext-configure zip --with-libzip \
  && docker-php-ext-install zip \
  && pecl install ev mongodb redis xdebug amqp \
  && echo "extension=ev.so" >> /usr/local/etc/php/conf.d/90-ev.ini \
  && echo "extension=mongodb.so" >> /usr/local/etc/php/conf.d/90-mongodb.ini \
  && echo "extension=redis.so" >> /usr/local/etc/php/conf.d/90-redis.ini \
  && echo "extension=amqp.so" >> /usr/local/etc/php/conf.d/90-amqp.ini \
  && sh /root/composer.sh \
  && composer global require hirak/prestissimo \
  && apk del .build-deps \
  && rm -rf /var/cache/apk/* /var/tmp/* /tmp/* /app/config \
  && chmod -R 777 /tmp

WORKDIR "/application"
