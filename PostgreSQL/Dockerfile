FROM ubuntu:14.04
MAINTAINER Howard Deiner

# Install PostgreSQL
# See https://help.ubuntu.com/community/PostgreSQL
RUN sudo apt-get update
RUN sudo apt-get -y install postgresql postgresql-contrib pgadmin3

# Allow port 80 and 5432 for communication.  
EXPOSE 80
EXPOSE 5432

# Default service
CMD ["service", "postgresql", "start"]
