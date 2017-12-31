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
