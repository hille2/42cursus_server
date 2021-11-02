
FROM alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

ARG		user
ARG		ssl_body

ENV		USER=${user}
ENV		SSL_BODY=${ssl_body}

RUN		apk update &&\
		apk add --no-cache nginx openssl &&\
		mkdir -p /run/nginx &&\
		mkdir /var/www/42.fr

COPY	/index.html /var/www/42.fr/
COPY	/Intra /var/www/42.fr/
COPY	/nginx.conf /etc/nginx

RUN		openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj \
		"${SSL_BODY}" \
		-keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt 

EXPOSE 80 443
CMD nginx -g "daemon off;"