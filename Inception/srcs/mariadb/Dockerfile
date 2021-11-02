FROM alpine:3.12

MAINTAINER ${USER} <sgath@student.21-school.ru>


RUN		apk update &&\ 
		apk add --no-cache mysql mysql-client

RUN mysql_install_db --user=mysql

COPY	/my.cnf /etc/my.cnf
COPY	/mysql-svc.sql .

VOLUME /var/lib/mysql

RUN mysqld & sleep 5

#RUN mysql < /mysql-svc.sql
#RUN pkill mysqld & sleep 5
ENTRYPOINT ["mysqld_safe"]
#CMD 	/usr/bin/mysqld_safe
#./setup.sh