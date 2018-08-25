FROM debian:jessie-slim
MAINTAINER Sebastian Koltun

RUN apt-get update

RUN yes | apt-get install wget

  # Download OpenJDK 10
RUN wget https://download.java.net/java/GA/jdk10/10.0.2/19aef61b38124481863b1413dce1855f/13/openjdk-10.0.2_linux-x64_bin.tar.gz

  #Unpack Java
RUN mkdir -p usr/local/java && tar zxf openjdk-10.0.2_linux-x64_bin.tar.gz -C /usr/local/java
RUN chown -R root:root usr/local/java/jdk-10.0.2/*
RUN chmod -R a+rx usr/local/java/jdk-10.0.2/*

  # Add jboss user
RUN groupadd -r jboss -g 1000 && useradd -u 1000 -r -g jboss -m -d /opt/jboss -s /sbin/nologin -c "JBoss user" jboss && \
chmod 755 /opt/jboss

USER jboss

  # Set JAVA_HOME
ENV JAVA_INSTALL_DIR=/usr/local/java/jdk-10.0.2

  # Set the working directory to jboss
WORKDIR /opt/jboss
