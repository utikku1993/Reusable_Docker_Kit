FROM ubuntu:18.04
MAINTAINER Uttakarsh Tikku

# Debian Prep
RUN apt-get clean && apt-get update -y && apt-get upgrade -y
RUN apt-get install -y libnss3-dev fonts-liberation libappindicator3-1 libasound2 libatk-bridge2.0-0 libatspi2.0-0 libgtk-3-0 libx11-xcb1 libxtst6 lsb-release xdg-utils xvfb

RUN mkdir -p /opt
COPY solr-8.4.1 /opt/solr

RUN apt-get update
RUN apt-get --yes install openjdk-8-jdk