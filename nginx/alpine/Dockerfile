FROM nginx:alpine

LABEL maintainer="emin şen"
LABEL maintainer.author="contact@emnsen.com"

ENV NAME emn

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/${NAME}-access.log \
	&& ln -sf /dev/stderr /var/log/nginx/${NAME}-error.log

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]