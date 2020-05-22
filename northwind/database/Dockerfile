FROM mysql:5.7

#set myswl root p/d to changeit
ENV MYSQL_ROOT_PASSWORD=changeit

#write one or more docker command to copy *.sql into /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

HEALTHCHECK --interval=30s --timeout=5s  --start-period=5s \
--retries=3 CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

#where mysql stores the database
VOLUME /var/lib/mysql


#exec in and run mysql -uroot -pchangeit