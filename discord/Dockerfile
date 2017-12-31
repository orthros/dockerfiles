# DESCRIPTION:	  Create the Discord editor in a container
# AUTHOR:		  Colin Nelson <colin@ifdevthentalk.com>
# COMMENTS:
#	This file describes how to build the discord message client
#	in a container with all dependencies installed.
#	Note: discord is not a node-webkit app,
#	it uses electron(https://github.com/atom/electron)
#	Tested on Ubuntu Xenial.
# USAGE:
#	# Download discord Dockerfile
#	wget https://raw.githubusercontent.com/orthros/dockerfiles/master/discord/Dockerfile
#
#	# Build discord image
#	docker build -t discord .
#
#	docker run -d \
#        --net host \
#        -v /etc/localtime:/etc/localtime:ro \
#        -v /tmp/.X11-unix:/tmp/.X11-unix \
#        -e "DISPLAY=unix${DISPLAY}" \
#        -e QT_DEVICE_PIXEL_RATIO \
#        --device /dev/snd \
#        --device /dev/dri \
#        --name discord \
#        discord
#

FROM ubuntu:xenial

LABEL maintainer "Colin Nelson <colin@ifdevthentalk.com>"

RUN apt-get update && \
    apt-get install -y \
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

RUN curl -Lo discord.deb 'https://discordapp.com/api/download?platform=linux&format=deb'

RUN dpkg -i discord.deb

CMD ["discord"]
