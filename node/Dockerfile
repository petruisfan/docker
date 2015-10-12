FROM debian:jessie

RUN apt-get update && apt-get install -y \
        curl \
        sudo \
        git \
        bzip2 \
        libfreetype6 libfreetype6-dev libfontconfig1 libfontconfig1-dev \
        build-essential \
        man tmux \
    && apt-get clean \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#ENV NODE_VERSION 0.12.7
ENV NODE_VERSION=4.1.2 \
    NPM_VERSION=2.1.16

RUN curl -SLO "http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.gz" \
    && tar -xzf "node-v$NODE_VERSION-linux-x64.tar.gz" -C /usr/local --strip-components=1 \
    && rm "node-v$NODE_VERSION-linux-x64.tar.gz" \
    && npm install -g npm@"$NPM_VERSION" \
    && npm install -g gulp grunt-cli bower yo generator-angular \
    && npm cache clear

RUN addgroup -gid 1000 petru \
    && adduser --uid 1000 --gid 1000 --disabled-password --gecos '' petru \
    && adduser petru sudo \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN echo "alias ll='ls -la --color=auto'" >> /home/petru/.bashrc
RUN echo "alias ..='cd ..'" >> /home/petru/.bashrc
