FROM ubuntu:14.04
MAINTAINER Howard Deiner

# Install Monngo
# See http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/
# Import MongoDB public GPG key AND create a MongoDB list file
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
RUN echo "deb http://repo.mongodb.org/apt/ubuntu $(cat /etc/lsb-release | grep DISTRIB_CODENAME | cut -d= -f2)/mongodb-org/3.2 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.2.list
RUN apt-get update && apt-get install -y mongodb-org && mkdir -p /data/db

# Mongo communicates over port 27017
EXPOSE 27017

# Set /usr/bin/mongod as the dockerized entry-point application
ENTRYPOINT ["/usr/bin/mongod"]

# on host:
#
# to build (from dbSetup directory):
# docker build -t mongodb:latest MongoDB
#
# to run:
# docker run -p 27017:27017 mongodb:latest
#
# and don't forget about:
# docker stop $(docker ps -a -q)
# docker rm $(docker ps -a -q)
