FROM	alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

ARG		USER
ARG		SSL_BODY
ARG		DOMAIN

ENV		USER=${USER}
ENV		SSL_BODY=${SSL_BODY}
ENV		DOMAIN=${DOMAIN}

RUN		apk update &&\
		apk add --no-cache nginx openssl &&\
		mkdir -p /run/nginx &&\
		mkdir /var/www/${DOMAIN}

COPY 	/nginx.conf /etc/nginx/
COPY 	/index.html /var/www/${DOMAIN}/index.html

RUN 	mkdir /etc/nginx/ssl &&\
		openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj \
		"${SSL_BODY}" \
		-keyout /etc/nginx/ssl/server.key -out /etc/nginx/ssl/server.crt

EXPOSE	80

CMD		nginx -g 'daemon off;'