FROM ubuntu:precise
MAINTAINER Nicolas Favre-Felix <n.favrefelix@gmail.com>

# Install dependencies
RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" >> /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y wget openjdk-7-jre-headless dnsmasq-base

# Install Cassandra
ADD bin/install-cassandra /usr/bin/install-cassandra
RUN install-cassandra 2.0.2

# Install start scripts and hosts file
ADD bin/pipework /usr/bin/
ADD bin/start-cassandra /usr/bin/
ADD bin/run-command /usr/bin/

# Configure host names
ADD etc/cassandra.hosts /etc/dnsmasq.d/0hosts
ADD etc/dnsmasq.conf /etc/dnsmasq.conf
ADD etc/resolv.conf /etc/resolv.dnsmasq.conf

EXPOSE 9160
