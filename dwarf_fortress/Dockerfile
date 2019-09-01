# DESCRIPTION:	  Create the Dwarf Fortress application in a container
# AUTHOR:		  Colin Nelson <colin@orthros.dev>
# COMMENTS:
#	This file describes how to build the Dwarf Fortress client
#	in a container with all dependencies installed.
#	Tested on Arch.
# USAGE:
#	# Download Dwarf Fortress Dockerfile
#	wget https://raw.githubusercontent.com/orthros/dockerfiles/master/dwarf_fortress/Dockerfile
#
#	# Build Dwarf Fortress image
#	docker build -t df .
#
#	docker run -d \
#        -v /etc/localtime:/etc/localtime:ro \
#        -v /tmp/.X11-unix:/tmp/.X11-unix \
#        -v "${HOME}/.config/df/data:/df_linux/data" \
#        -e "DISPLAY=unix${DISPLAY}" \
#        -e QT_DEVICE_PIXEL_RATIO \
#        --device /dev/snd \
#        --device /dev/dri \
#        --name df \
#        df
#

FROM debian:stretch as BASE

ENV DF_VERSION=44_12

RUN apt update && \
	apt install -y \
				libgtk2.0-0 \
				libglu1-mesa \
				libsdl1.2debian \
				libsdl-image1.2 \
				libsdl-ttf2.0-0 \
				libopenal1 \
				libsndfile1 \
				libncursesw5 \
				bzip2 \
				curl

FROM BASE as BUILDER

RUN curl -LSsO http://www.bay12games.com/dwarves/df_${DF_VERSION}_linux.tar.bz2

RUN tar -xjf df_${DF_VERSION}_linux.tar.bz2

FROM BASE as FINAL

COPY --from=BUILDER /df_linux ./df_linux

ENTRYPOINT "/df_linux/df"
