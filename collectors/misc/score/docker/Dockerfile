
FROM docker.io/openjdk:8-jdk-alpine

MAINTAINER Hygieia@capitalone.com

RUN \
  mkdir /hygieia

COPY *.jar /hygieia/
COPY properties-builder.sh /hygieia/
COPY logback.xml /hygieia/

WORKDIR /hygieia

VOLUME ["/hygieia/logs"]

CMD ./properties-builder.sh && \
  java -Dlogging.config=file:/hygieia/logback.xml -jar score-collector*.jar --spring.config.location=/hygieia/hygieia-score-collector.properties

