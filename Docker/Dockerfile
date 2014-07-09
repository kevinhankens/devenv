FROM ubuntu:latest

# MAINTAINER Tyler Cipriani, tyler@tylercipriani.com

# Download and install php, nginx, and supervisor, hey, just linux for a change!
RUN apt-get update
RUN apt-get install -y software-properties-common
RUN apt-get update
RUN apt-get -y dist-upgrade
RUN apt-get install -y vim build-essential
RUN apt-get install -y apache2 libapache2-mod-php5 mysql-server mysql-client php5 php5-gd php5-mysql php5-curl php5-cli php5-cgi php5-dev
RUN apt-get install -y curl
RUN apt-get install -y git

RUN /bin/bash -l -c 'useradd -s /bin/bash -m -d /home/khankens -c "Kevin Hankens" khankens'

RUN /bin/bash -l -c '\curl -sSL https://get.rvm.io | bash -s stable'
RUN /bin/bash -l -c 'rvm requirements'
RUN /bin/bash -l -c 'rvm install 2.1'

# Setup config files
ADD ./bash/.bashrc /home/khankens/.bashrc
ADD ./bash/.bash_aliases /home/khankens/.bash_aliases

# Shared volume
RUN mkdir -p /var/www
VOLUME ["/var/www"]

# Default command for container, start supervisor
CMD /bin/bash
USER root

# Expose port 80 of the container
EXPOSE 80

