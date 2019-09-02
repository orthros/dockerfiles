# DESCRIPTION:	  Create the Dungeon Crawl Stone Soup application in a container
# AUTHOR:		  Colin Nelson <colin@orthros.dev>
# COMMENTS:
#	This file describes how to build the Dungeon Crawl Stone Soup client
#	in a container with all dependencies installed.
#	Tested on Arch.
# USAGE:
#	# Download Dungeon Crawl Stone Soup Dockerfile
#	wget https://raw.githubusercontent.com/orthros/dockerfiles/master/crawldcss/Dockerfile
#
#	# Build Dungeon Crawl Stone Soup image
#	docker build -t crawldcss .
#
#	docker run -d \
#        -v /etc/localtime:/etc/localtime:ro \
#        --device /dev/snd \
#        --device /dev/dri \
#        --name crawldcss \
#        crawldcss
#
FROM debian:latest

RUN apt-get update && apt-get install -y wget gnupg apt-transport-https

# Install the source repository
RUN echo 'deb https://crawl.develz.org/debian crawl 0.21' | tee -a /etc/apt/sources.list
# Install the DCSS signing key
RUN wget https://crawl.develz.org/debian/pubkey -O - | apt-key add -
# update your package list
RUN apt-get update
# install console version
RUN apt-get install -y crawl

CMD ["/usr/games/crawl" ]
