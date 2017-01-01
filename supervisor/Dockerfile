# yohayashi/supervisor

FROM yohayashi/jupyter

MAINTAINER Yoshihiro Hayashi <yohayashi@gmail.com>

USER root

RUN apt-get install -y supervisor
RUN sed -i 's/^\(\[supervisord\]\)$/\1\nnodaemon=true/' /etc/supervisor/supervisord.conf

VOLUME ["/etc/supervisor/conf.d"]

# ADD conf/cloud9.conf /etc/supervisor/conf.d/
# ADD conf/jupyter.conf /etc/supervisor/conf.d/

ENV TINI_VERSION v0.13.2
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini

ENTRYPOINT ["tini", "--"]
CMD ["supervisord", "-c", "/etc/supervisor/supervisord.conf"]