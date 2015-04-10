# docker-creator

The collection of scripts for docker creation. 

WARNING! Experimental project. Please don't use it in production.

Based on [rerun](https://github.com/rerun/rerun) framework. 

## How to use docker-creator from command line

```sh
$ ./rerun 
Available modules:
  install: "Module for simplifying installation component(-s) inside of Docker" - 0.0.1
  misc: "Module for service commands" - 0.0.1
$
$ ./rerun misc
Available commands in module, "misc":
clean: "Clean temporary directories"
$
$ ./rerun install
Available commands in module, "install":
oracle-java: "Install Oracle Java: JDK, JRE, Server JRE"
tomcat: "Install Apache Tomcat"
zookeeper: "Install Apache Zookeeper"
$
$ ./rerun install:zookeeper
Error! Please specify ZooKeeper version
usage: ./rerun install:zookeeper <version>

The list of available packages:
  3.3.3  3.3.4  3.3.5  3.3.6  3.4.0  3.4.1  3.4.2  3.4.3  3.4.4  3.4.5  3.4.6
```

## How to use docker-creator into Dockerfile (example)

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
