FROM ubuntu:14.04
MAINTAINER Howard Deiner

# Install MySQL
# See https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-14-04
RUN DEBIAN_FRONTEND=noninteractive apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -q -y install mysql-server && DEBIAN_FRONTEND=noninteractive mysql_install_db
RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf
RUN /usr/sbin/mysqld & sleep 10s && echo "GRANT ALL ON *.* TO admin@'%' IDENTIFIED BY 'changeme' WITH GRANT OPTION; FLUSH PRIVILEGES" | mysql

# mysql client connect over port 3306
EXPOSE 3306

# Default service
CMD ["/usr/bin/mysqld_safe"]

# on host:
#
# to build (from dbSetup directory):
# docker build -t mysql:latest MySQL
#
# to run:
# docker run -p 3306:3306 mysql:latest
#
# to start a client, try:
# mysql --protocol=tcp --port=3306 -u admin -p
#
# the password for admin is changeme
#
# and don't forget about:
# docker stop $(docker ps -a -q)
# docker rm $(docker ps -a -q)
