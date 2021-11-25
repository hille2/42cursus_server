
FROM alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

ARG		user
ARG		ssl_body

#ENV		USER=${user}
#ENV		SSL_BODY=${ssl_body}
ENV		SSL_BODY="/C=RU/ST=Republic_of_Tatarstan/L=Kazan/O=Ecole42/OU=School21/CN=sgath/emailAddress=sgath@student.21-school.ru"
ENV		USER=sgath

RUN		apk update &&\
		apk add --no-cache nginx openssl &&\
		mkdir -p /run/nginx &&\
		mkdir -p /var/www/42.fr/ &&\
		chmod +x /var/www/42.fr/

COPY	/nginx.conf /etc/nginx/conf.d/default.conf


RUN		openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj \
		"${SSL_BODY}" \
		-keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt 

#EXPOSE 443

CMD nginx -g "daemon off;"