FROM alpine:3.12

MAINTAINER sgath <sgath@student.21-school.ru>

RUN apk update && apk add --no-cache mysql mysql-client

COPY /mysql.sh ./mysql.sh
COPY /my.cnf /etc/my.cnf

COPY /mysql-svc.sql ./mysql-svc.sql

RUN chmod +x ./mysql.sh &&\
	chmod +x /etc/my.cnf

RUN mkdir /run/mysqld &&\
	chmod +x /run/mysqld
EXPOSE 3306
CMD ./mysql.sh
