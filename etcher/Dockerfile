# DESCRIPTION:	  Create the Etcher application in a container
# AUTHOR:		  Colin Nelson <colin@ifdevthentalk.com>
# COMMENTS:
#	This file describes how to build the Etcher application
#	in a container with all dependencies installed.
#	Note: Etcher is not a node-webkit app,
#	it uses electron(https://github.com/atom/electron)
#	Tested on Ubuntu Xenial.
# USAGE:
#	# Download Etcher Dockerfile
#	wget https://raw.githubusercontent.com/orthros/dockerfiles/master/etcher/Dockerfile
#
#	# Build etcher image
#	docker build -t etcher .
#
#	docker run -d \
#        --net host \
#        -v /etc/localtime:/etc/localtime:ro \
#        -v /tmp/.X11-unix:/tmp/.X11-unix \
#        -e "DISPLAY=unix${DISPLAY}" \
#        -e QT_DEVICE_PIXEL_RATIO \
#        --device /dev/snd \
#        --device /dev/dri \
#        --device /dev/usb \
#        --name etcher \
#        etcher
#

FROM ubuntu:xenial

LABEL maintainer "Colin Nelson <colinnlsn@gmail.com>"

RUN apt-get update \
    && apt-get install -y apt-transport-https 

RUN echo "deb https://dl.bintray.com/resin-io/debian stable etcher" | tee /etc/apt/sources.list.d/etcher.list \
    && apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 379CE192D401AB61 \
    && apt-get update \
    && apt-get install -y etcher-electron

# Add a user
ENV HOME /home/etcher
RUN useradd --create-home --home-dir $HOME etcher \
     && chown -R etcher:etcher $HOME

WORKDIR $HOME

USER etcher

CMD ["etcher-electron"]
