FROM	alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

ENV		SSL_BODY="/C=RU/ST=Republic_of_Tatarstan/L=Kazan/O=Ecole42/OU=School21/CN=sgath/emailAddress=sgath@student.21-school.ru"

RUN		apk update &&\
		apk add --no-cache nginx openssl &&\
		mkdir -p /run/nginx &&\
		mkdir /var/www/${USER}42.fr

COPY 	/nginx.conf /etc/nginx/
COPY 	/index.html /var/www/${USER}42.fr/index.html
RUN 	openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj \
		"${SSL_BODY}" \
		-keyout /etc/ssl/private/example.org.key -out /etc/ssl/example.org.crt

CMD		nginx -g 'daemon off;'