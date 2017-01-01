# yohayashi/python

FROM ubuntu:xenial
MAINTAINER Yoshihiro Hayashi <yohayashi@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

ARG USER=user
ARG PASSWORD=password

ENV USER $USER
ENV HOME /home/$USER
ENV PYENVPATH $HOME/.pyenv
ENV PATH $PYENVPATH/shims:$PYENVPATH/bin:$PATH

RUN apt-get update && apt-get install -y sudo
RUN groupadd -g 1000 $USER && \
    useradd -g $USER -G sudo -m -s /bin/bash $USER && \
    echo "$USER:$PASSWORD" | chpasswd

RUN apt-get update && apt-get install -y git vim make build-essential libssl-dev zlib1g-dev libbz2-dev \
    libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils
    
USER $USER

RUN curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash

RUN echo 'eval "$(pyenv init -)"' >  $HOME/.bashrc

RUN pyenv install 2.7.13
RUN pyenv global 2.7.13

RUN pip install --upgrade pip setuptools
RUN mkdir -p $HOME/.config/pip
RUN echo "[list]\nformat=legacy"  >> $HOME/.config/pip/pip.conf