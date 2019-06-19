FROM 90pixel/php-fpm

LABEL maintainer="emin şen"
LABEL maintainer.author="contact@emnsen.com"

RUN apk --update --no-cache add --virtual .build-deps gcc make g++ ruby-dev ruby-rdoc \
	automake \
	alpine-sdk  \
	nasm  \
	autoconf  \
	build-base \
	zlib \
	zlib-dev \
	libpng \
	libpng-dev\
	libwebp \
	libwebp-dev \
	libjpeg-turbo \
	libjpeg-turbo-dev \
	&& apk add nodejs npm yarn ruby rsync \
	&& gem install sass scss_lint \
	&& yarn global add gulp-cli pm2 shipit-cli shipit-deploy optipng-bin \
	&& apk del .build-deps \
	&& rm -rf /var/cache/apk/* /var/tmp/* /tmp/* /app/config
