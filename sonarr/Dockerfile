FROM ubuntu:trusty
MAINTAINER Coaxial <coaxial@cxial.tk>

ENV DEBIAN_FRONTED noninteractive
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FDA5DFFC && \
    echo "deb http://apt.sonarr.tv/ master main" | sudo tee /etc/apt/sources.list.d/sonarr.list && \
    apt-get update && \
    apt-get install -yq nzbdrone && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*

# RUN chown -R nobody:users /opt/NzbDrone ; \
#     mkdir /storage /config && \
#     chown -R nobody:users /storage && \
#     chown -R nobody:users /config

# # There is no official way to specify the config directory to Sonarr
# # So we'll put a symbolic link where Sonarr expects its config dir, pointing to the docker volume
# RUN mkdir -p /root/.config && \
#     [ ! -L /root/.config/NzbDrone ] && ln -s /config /root/.config/NzbDrone

VOLUME ["/config", "/storage"]

EXPOSE 8989

# USER nobody

# CMD ["/usr/bin/mono", "--debug", "/opt/NzbDrone/NzbDrone.exe", "-data=/config"]
CMD ["/usr/bin/mono", "/opt/NzbDrone/NzbDrone.exe"]
