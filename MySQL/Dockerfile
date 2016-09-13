FROM ubuntu:14.04
MAINTAINER Howard Deiner

# Install MySQL
# See https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-14-04
RUN export DEBIAN_FRONTEND=noninteractive
RUN apt-get update
RUN apt-get -q -y install mysql-server 
RUN mysql_install_db
RUN /etc/init.d/mysql start

# Allow port 80 and 3306 for communication.  
EXPOSE 80
EXPOSE 3306

# Default service
CMD ["/etc/init.d/mysql", "start"]
