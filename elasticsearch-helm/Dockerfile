FROM ubuntu:16.04
MAINTAINER Barnaby Gray <barnaby@pickle.me.uk>

# enable universe
RUN sed 's/main$/main universe/' -i /etc/apt/sources.list
RUN apt-get update

RUN apt-get install -y openjdk-8-jre && apt-get clean

# just for testing
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

# Elasticsearch
# docker pull barnybug/elasticsearch
#FROM barnybug/openjdk-7-jre
#FROM picoded/ubuntu-openjdk-8-jdk
#MAINTAINER Barnaby Gray <barnaby@pickle.me.uk>

# install wget
RUN apt-get install -y wget && apt-get clean

# download and unpack elasticsearch
RUN wget -q https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.2.1.tar.gz -O - | tar zxvf -
# create directories with access rights for 'nobody'
RUN mkdir -m 777 elasticsearch-1.2.1/logs elasticsearch-1.2.1/data

EXPOSE 9200 9300
CMD ["elasticsearch-1.2.1/bin/elasticsearch"]
