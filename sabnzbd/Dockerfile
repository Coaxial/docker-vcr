FROM ubuntu:trusty
MAINTAINER Coaxial <coaxial@cxial.tk>

ENV DEBIAN_FRONTEND noninteractive
RUN echo "deb http://archive.ubuntu.com/ubuntu trusty multiverse" >> /etc/apt/sources.list && \
    apt-get -q update && \
    apt-get install -qy software-properties-common python-software-properties && \
    add-apt-repository -y  ppa:jcfp/ppa && \
    apt-get -q update && \
    apt-get install -qy sabnzbdplus sabnzbdplus-theme-classic sabnzbdplus-theme-mobile sabnzbdplus-theme-plush \
    par2 python-yenc unzip unrar && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*

VOLUME ["/config","/storage"]

EXPOSE 8080 9090

CMD ["/usr/bin/sabnzbdplus","--config-file","/config","--server","0.0.0.0:8080","--console","--browser","0"]
