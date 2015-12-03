FROM debian:jessie

ENV USER petru

ENV MONGO_MAJOR 3.0
ENV MONGO_VERSION 3.0.6


RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates curl numactl \
    && rm -rf /var/lib/apt/lists/*

# gpg: key 7F0CEB10: public key "Richard Kreuter <richard@10gen.com>" imported
RUN apt-key adv --keyserver ha.pool.sks-keyservers.net --recv-keys 492EAFE8CD016A07919F1D2B9ECBEC467F0CEB10

RUN echo "deb http://repo.mongodb.org/apt/debian wheezy/mongodb-org/$MONGO_MAJOR main" > /etc/apt/sources.list.d/mongodb-org.list

RUN set -x \
    && apt-get update \
    && apt-get install -y --force-yes \
        mongodb-org-shell=$MONGO_VERSION \
        mongodb-org-tools=$MONGO_VERSION \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /var/lib/mongodb \
    && apt-get clean

RUN addgroup -gid 1000 $USER \
    && adduser --uid 1000 --gid 1000 --disabled-password --gecos '' $USER \
    && adduser $USER sudo \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN echo "alias ll='ls -la --color=auto'" >> /home/$USER/.bashrc
RUN echo "alias ..='cd ..'" >> /home/$USER/.bashrc

