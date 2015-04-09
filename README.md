# docker-creator

The collection of scripts for docker creation. 

WARNING! Experimental project. Please don't use it in production.

Based on [rerun](https://github.com/rerun/rerun) framework. 

## How to use (example)

```
FROM ubuntu:trusty

RUN apt-get install -y wget

RUN mkdir -p /deploy/
RUN wget -qO - https://github.com/ownport/docker-creator/archive/master.tar.gz | tar xvz -C /deploy/

RUN /deploy/docker-creator-master/rerun install:oracle-java 7u76:Server-JRE
RUN /deploy/docker-creator-master/rerun misc:clean

ENV JAVA_HOME /opt/jdk1.7.0_76
ENV PATH $JAVA_HOME/bin:$PATH
```
