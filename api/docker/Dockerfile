FROM docker.io/openjdk:8-jre-alpine

MAINTAINER Hygieia@capitalone.com

RUN apk add --no-cache bash

RUN mkdir /hygieia /hygieia/config

COPY hygieia/ /hygieia
COPY properties-builder.sh /hygieia/
COPY logback.xml /hygieia/

WORKDIR /hygieia

VOLUME ["/hygieia/logs"]

ENV PROP_FILE /hygieia/config/application.properties

EXPOSE 8080
CMD ./properties-builder.sh &&\
  java -Djava.security.egd=file:/dev/./urandom -Dlogging.config=file:/hygieia/logback.xml -jar api.jar --spring.config.location=$PROP_FILE
