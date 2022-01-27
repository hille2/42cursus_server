
FROM alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

ARG		user
ARG		ssl_body
ARG		domian

ENV		USER=${user}
ENV		SSL_BODY=${ssl_body}
ENV 	DOMIAN=${domian}

RUN		apk update &&\
		apk add --no-cache nginx openssl  gettext-base &&\
		mkdir -p /run/nginx &&\
		mkdir -p /var/www/42.fr/ &&\
		chmod +x /var/www/42.fr/

COPY	/default.conf /etc/nginx/conf.d/default.conf
COPY	./index.html /var/www/${DOMIAN}/wordpress/index.html

RUN		openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj \
		"${SSL_BODY}" \
		-keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt 

RUN		envsubst < /etc/nginx/conf.d/default.conf > /etc/nginx/nginx.conf

#EXPOSE 443

CMD nginx -g "daemon off;"