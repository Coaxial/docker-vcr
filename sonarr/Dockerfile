FROM debian:jessie
MAINTAINER Coaxial <coaxial@cxial.tk>

ENV DEBIAN_FRONTED noninteractive
# FROM debian:jessie
 
# add keys for xamarin and sonarr
# add xamarin repositories, including libjpeg override
# add the sonarr repository, develop branch (replace develop with 'master' for stable
 
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D3D831EF FDA5DFFC \
 && echo "deb http://download.mono-project.com/repo/debian wheezy main" | tee /etc/apt/sources.list.d/mono-xamarin.list \
 && echo "deb http://download.mono-project.com/repo/debian wheezy-libjpeg62-compat main" | tee -a /etc/apt/sources.list.d/mono-xamarin.list \
 && echo "deb http://apt.sonarr.tv/ develop main" | tee /etc/apt/sources.list.d/sonarr.list
 
RUN apt-get update -q && apt-get install -qy nzbdrone
 
# add service user and group, hardcode to our uid/gid for now.
RUN groupadd -g 5000 sonarr && useradd -u 5000 -g sonarr -b /opt -s /bin/bash -m sonarr && \
    chown sonarr:sonarr -R /opt/sonarr
# USER sonarr
WORKDIR /opt/sonarr
 
# external interface
# VOLUME /opt/sonarr/data /media/TV-inbox /media/TV-trash /media/TV
# EXPOSE 8989
 
#ENTRYPOINT ["mono", "/opt/NzbDrone/NzbDrone.exe"]


# RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FDA5DFFC && \
#     echo "deb http://apt.sonarr.tv/ master main" | sudo tee /etc/apt/sources.list.d/sonarr.list && \
#     apt-get update && \
#     apt-get install -yq nzbdrone && \
#     apt-get clean && \
#     rm -rf /var/lib/apt/lists/* && \
#     rm -rf /tmp/*

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
