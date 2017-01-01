# yohayashi/cloud9

FROM yohayashi/python
MAINTAINER Yoshihiro Hayashi <yohayashi@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

USER root

RUN wget 'https://nodejs.org/dist/v0.12.18/node-v0.12.18-linux-x64.tar.xz' && \
    tar -xJf node-v0.12.18-linux-x64.tar.xz -C /usr/local --strip-components=1 && \
    ln -s /usr/local/bin/node /usr/local/bin/nodejs && \
    rm node-v0.12.18-linux-x64.tar.xz
    
RUN mkdir /cloud9 && chown -R $USER:$USER /cloud9

USER $USER

RUN git clone git://github.com/c9/core.git /cloud9 && \
    /cloud9/scripts/install-sdk.sh