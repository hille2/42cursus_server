FROM alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

RUN		apk update && apk add --no-cache php7-fpm php7-common php7-session php7-iconv php7-json \ 
		php7-gd php7-curl php7-xml php7-mysqli php7-imap php7-cgi fcgi php7-pdo \
		php7-pdo_mysql php7-soap php7-xmlrpc php7-posix php7-mcrypt php7-gettext \
		php7-ldap php7-ctype php7-dom php7-mbstring\
		wget 
RUN 	wget http://wordpress.org/latest.tar.gz && tar -xzvf latest.tar.gz &&\
		rm latest.tar.gz &&\
		mkdir -p  /var/www/42.fr/wordpress &&\
		mv /wordpress /var/www/42.fr/ &&\
		chmod 777 -R /var/www/42.fr/wordpress
#COPY 	/wp-config.php /var/www/42.fr/wordpress
COPY 	./www.conf /etc/php/7.3/fpm/pool.d/
#RUN 	chmod +x /var/www/42.fr/wordpress/wp-config.php 
copy 	index.php /var/www/42.fr/wordpress
EXPOSE	9000
CMD		php-fpm7 -F
