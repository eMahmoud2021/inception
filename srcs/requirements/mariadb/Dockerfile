FROM debian:buster

RUN	apt-get update && \
	apt-get install -y \
	mariadb-server \
	mariadb-client

RUN	mkdir -p /run/mysqld /var/lib/mysql && \
	chown -R mysql:mysql /run/mysqld /var/lib/mysql

RUN	mysql_install_db --user=mysql --datadir=/var/lib/mysql --auth-root-authentication-method=normal --skip-test-db

COPY ./conf/my.cnf /etc/mysql/my.cnf

COPY ./tools/setup_mariadb.sh /usr/local/bin/

EXPOSE 3306

ENTRYPOINT ["setup_mariadb.sh"]

CMD ["/usr/bin/mysqld_safe", "--datadir=/var/lib/mysql"]
