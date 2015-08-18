FROM ubuntu:trusty
MAINTAINER Coaxial <coaxial@cxial.tk>

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update -q && \
    apt-get install -yq git python && \
    git clone https://github.com/RuudBurger/CouchPotatoServer.git /CouchPotatoServer && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*

VOLUME ["/config", "/storage"]

EXPOSE 5050

CMD ["/usr/bin/python", "/CouchPotatoServer/CouchPotato.py", "--data_dir", "/config/", "--config_file", "/config/settings.conf", "--console_log"]
