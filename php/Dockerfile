FROM php:7.2-fpm

LABEL maintainer="emin şen"
LABEL maintainer.author="contact@emnsen.com"

ENV COMPOSER_ALLOW_SUPERUSER=1

ADD composer.sh /root/

RUN buildDeps="\
    libbz2-dev \
    libmemcached-dev \
    default-libmysqlclient-dev \
    libsasl2-dev \
    " \
    runtimeDeps="\
    curl \
    git \
    libfreetype6-dev \
    libicu-dev \
    libjpeg-dev \
    libmcrypt-dev \
    libmemcachedutil2 \
    libpng-dev \
    libpq-dev \
    libxml2-dev \
    cron \
    mysql-client \
    libzmq3-dev \
    supervisor \
    libevent-2.0-5 \
    libevent-dev \
    libssl-dev \
    " \
    && apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y $buildDeps $runtimeDeps zip unzip \
    && docker-php-ext-install bcmath bz2 calendar exif iconv intl mbstring mysqli opcache pdo pdo_mysql pdo_pgsql pgsql soap zip sockets pcntl \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && pecl install memcached redis xdebug ev event-2.3.0 zmq-beta mongodb \
    && docker-php-ext-enable memcached.so redis.so xdebug.so ev.so event.so zmq.so mongodb.so \
    && apt-get purge -y --auto-remove $buildDeps \
    && rm -r /var/lib/apt/lists/* \
    && curl -L http://cs.sensiolabs.org/download/php-cs-fixer-v2.phar > /usr/local/bin/php-cs-fixer \
    && chmod +x /usr/local/bin/php-cs-fixer \
    && curl -L https://phar.phpunit.de/phpunit.phar > /usr/local/bin/phpunit \
    && chmod +x /usr/local/bin/phpunit \
    && bash /root/composer.sh \
    && rm -rf /var/cache/apk/* /var/tmp/* /tmp/*

WORKDIR "/application"
