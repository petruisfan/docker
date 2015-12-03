FROM debian:jessie

ENV USER petru

RUN apt-get update
RUN apt-get install -y sudo adduser ruby ruby-dev build-essential

RUN addgroup -gid 1000 $USER \
    && adduser --uid 1000 --gid 1000 --disabled-password --gecos '' $USER \
    && adduser $USER sudo \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN echo "alias ll='ls -la --color=auto'" >> /home/$USER/.bashrc
RUN echo "alias ..='cd ..'" >> /home/$USER/.bashrc

RUN gem install sass \
    && gem install compass

