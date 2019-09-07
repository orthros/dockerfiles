# DESCRIPTION:	  Create the postman application in a container
# AUTHOR:		  Colin Nelson <colin@orthros.dev>
# COMMENTS:
#	This file describes how to build the Postman client
#	in a container with all dependencies installed.
#	Note: postman is not a node-webkit app,
#	it uses electron(https://github.com/atom/electron)
#	Tested on Ubuntu Xenial.
# USAGE:
#	# Download postman Dockerfile
#	wget https://raw.githubusercontent.com/orthros/dockerfiles/master/postman/Dockerfile
#
#	# Build postman image
#	docker build -t postman .
#
#	docker run -d \
#        --net host \
#        -v /etc/localtime:/etc/localtime:ro \
#        -v /tmp/.X11-unix:/tmp/.X11-unix \
#        -v ~/.config:~/.config \
#        -e "DISPLAY=unix${DISPLAY}" \
#        -e QT_DEVICE_PIXEL_RATIO \
#        --device /dev/snd \
#        --device /dev/dri \
#        --name postman \
#        postman
#

FROM debian:stretch-slim

LABEL maintainer "Colin Nelson <colin@orthros.dev>"

RUN apt-get update && \
    apt-get install -y \
        procps \
        ca-certificates \
        apt-transport-https \
        libgconf-2-4 \
        libasound2 \
        libatomic1 \
        libnotify4 \
        libnspr4 \
        libnss3 \
        libxss1 \
        libxtst6 \
        libgtk2.0-0 \
        libnotify-bin \
        libnss3 \
        xvfb \
        libappindicator1 \
        libc++1 \
        curl \
        --no-install-recommends && \
    rm -rf /var/lib/apt/lists*

RUN update-ca-certificates

# Add a user
ENV HOME /home/postman
RUN useradd --create-home --home-dir $HOME postman \
     && chown -R postman:postman $HOME

WORKDIR $HOME

RUN curl -sSLo postman.tar.gz 'https://dl.pstmn.io/download/latest/linux64' && \
    tar -xzf postman.tar.gz && \
    rm postman.tar.gz && \
    ln -s $HOME/Postman/Postman /usr/bin/Postman

USER postman

# Start postman
CMD ["Postman"]
