FROM node:alpine

ENV DOMAIN=localhost
ENV webroot=
ENV serverroot=
ENV autoJoin=false
ENV autoJoinServer=
ENV autoJoinRoom=
ENV autoJoinPassword=

COPY run.sh /opt/run.sh

RUN apk add --no-cache git make g++ python \
  && cd /opt \
  && git clone https://github.com/lameeagl/synclounge.git \
  && cd synclounge \
  && npm install \
  && npm run build \
  && apk del make g++ python \
  && rm -rf /tmp/* /root/* \
  && chmod a+x /opt/run.sh

EXPOSE 8088 8089

CMD ["/opt/run.sh"]
