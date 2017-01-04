# yohayashi/python

FROM nginx
MAINTAINER Yoshihiro Hayashi <yohayashi@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN mkdir -p /etc/nginx/certs/
RUN openssl dhparam -out /etc/nginx/certs/dhparam.pem 2048
