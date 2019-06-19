FROM node:10-alpine

LABEL maintainer="emin şen"
LABEL maintainer.author="contact@emnsen.com"

RUN apk --no-cache add --virtual .build-deps autoconf gcc make g++ ruby-dev ruby-rdoc \
  && apk add ruby rsync curl openssh-client git \
  && gem install sass scss_lint \
  && yarn global add gulp-cli pm2 shipit-cli shipit-deploy \
  && apk del .build-deps \ 
  && rm -rf /var/cache/apk/* /var/tmp/* /tmp/* /app/config
