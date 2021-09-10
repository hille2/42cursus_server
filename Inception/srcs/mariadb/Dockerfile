FROM alpine:3.12

MAINTAINER ${MYSQL_USER} <sgath@student.21-school.ru>


RUN		apk update &&\ 
		apk add --no-cache mysql mysql-client
COPY	/my.cnf /etc/my.cnf
COPY	./setup.sh ./setup.sh
COPY	./mysql-svc.sql ./
RUN		mkdir -p /run/mysqld &&\
		chmod +x /run/mysqld &&\
		chmod +x /etc/my.cnf &&\
		chmod +x /mysql-svc.sql &&\
		chmod +x setup.sh
EXPOSE 	3306
CMD 	./setup.sh