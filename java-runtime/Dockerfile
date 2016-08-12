#
# Description:
#   Base image with Oracle JDK 8 
#
# Build: 
#   docker build -t nberthet/java-runtime .
#

FROM debian:jessie

RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" > /etc/apt/sources.list.d/webupd8team-java.list ;\
    echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" >> /etc/apt/sources.list.d/webupd8team-java.list ;\
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886 ;\
    apt-get update ;\
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections ;\
    apt-get install -y oracle-java8-installer libgtk2.0-0 libxtst6 curl \
 && rm /etc/apt/sources.list.d/webupd8team-java.list \
 && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
