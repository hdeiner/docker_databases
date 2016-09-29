FROM ubuntu:14.04
MAINTAINER Howard Deiner

# Install PostgreSQL
# See https://help.ubuntu.com/community/PostgreSQL
RUN apt-get update && apt-get -y install postgresql postgresql-contrib && echo "postgres:changeme" | chpasswd
RUN sed -i "s/^\#listen_addresses/listen_addresses/" /etc/postgresql/9.3/main/postgresql.conf
RUN sed -i "s/'localhost'/'*'/" /etc/postgresql/9.3/main/postgresql.conf
RUN echo 'host all all 0.0.0.0/0 trust' > /etc/postgresql/9.3/main/pg_hba.conf

# Allow 5432 for communication.
EXPOSE 5432

# Default service
CMD ["sudo", "-u", "postgres", "/usr/lib/postgresql/9.3/bin/postgres", "-D", "/var/lib/postgresql/9.3/main", "-c", "config_file=/etc/postgresql/9.3/main/postgresql.conf"]

# on host:
#
# to build (from dbSetup directory):
# docker build -t postgresql:latest PostgreSQL
#
# to run:
# docker run -d -p 5432:5432 postgresql:latest
#
# to start a client, try:
# psql --host=localhost --port=5432 --username=postgres -w
#
# the password for postgres is changeme
#
# and don't forget about:
# docker stop $(docker ps -a -q)
# docker rm $(docker ps -a -q)

