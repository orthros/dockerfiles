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
