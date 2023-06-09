FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=C.UTF-8

RUN \
  apt update && \
  apt install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    curl \
    git \
    sudo \
    && \
  rm -rf /var/lib/apt/lists/*

RUN \
  adduser --disabled-password --gecos "" user && \
  echo "user:user" | chpasswd && \
  usermod -aG sudo user && \
  echo "%sudo ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

RUN \
  curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - && \
  apt update && \
  apt install -y --no-install-recommends \
    nodejs \
    && \
  npm install --global yarn && \
  rm -rf /var/lib/apt/lists/*

USER user

RUN \
  mkdir /home/user/project

WORKDIR /home/user/project

CMD ["/bin/bash"]
