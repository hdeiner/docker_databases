FROM ubuntu:14.04
MAINTAINER Howard Deiner

# Install Monngo
# See https://docs.mongodb.com/v3.0/tutorial/install-mongodb-on-ubuntu/
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
RUN echo "deb http://repo.mongodb.com/apt/ubuntu trusty/mongodb-enterprise/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-enterprise.list
RUN apt-get update
RUN apt-get install -y mongodb

# Allow communication on ports 80 and 27107 
EXPOSE 80
EXPOSE 27017

# Default service
CMD ["service", "mongodb", "start"]
