FROM openjdk:8-jre-alpine
MAINTAINER Uttakarsh Tikku

ARG MIRROR=https://downloads.apache.org
ARG VERSION=3.6.0

LABEL name="zookeeper" version=3.5.5

RUN apk add --no-cache wget bash \
    && mkdir -p /opt/zookeeper \
    && wget -q -O - $MIRROR/zookeeper/zookeeper-$VERSION/apache-zookeeper-3.6.0-bin.tar.gz \
      | tar -xzC /opt/zookeeper --strip-components=1 \
    && cp /opt/zookeeper/conf/zoo_sample.cfg  /opt/zookeeper/conf/zoo.cfg \
    && mkdir -p /tmp/zookeeper

# Enable additional four-letter word commands
RUN echo "4lw.commands.whitelist=*" >> /opt/zookeeper/conf/zoo.cfg

EXPOSE 2181 2888 3888

WORKDIR /opt/zookeeper

HEALTHCHECK CMD [ $(echo ruok | nc 127.0.0.1:2181) == "imok" ] || exit 1

VOLUME ["/opt/zookeeper/conf", "/tmp/zookeeper"]

ENTRYPOINT ["/opt/zookeeper/bin/zkServer.sh"]
CMD ["start-foreground"]