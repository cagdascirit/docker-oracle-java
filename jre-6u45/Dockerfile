FROM debian:jessie

MAINTAINER Cagdas Cirit <cagdascirit@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

ENV VERSION 6
ENV UPDATE 45
ENV BUILD 06
ENV JAVA_VERSION ${VERSION}u${UPDATE}

RUN apt-get -y update && \
	apt-get -y install wget

RUN  wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}-b${BUILD}/jre-${JAVA_VERSION}-linux-x64.bin && \
	chmod +x jre-${JAVA_VERSION}-linux-x64.bin && \
	./jre-${JAVA_VERSION}-linux-x64.bin && \
	mkdir /usr/lib/jvm && \
	mv jre1* /usr/lib/jvm/jre-${VERSION}-oracle-x64 && \
	update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre-${VERSION}-oracle-x64/bin/java 100

RUN rm jre-${JAVA_VERSION}-linux-x64.bin && \
	apt-get -y remove wget && \
	apt-get -y --purge autoremove && \
	apt-get -y clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV JAVA_HOME /usr/lib/jvm/jre-${VERSION}-oracle-x64

ENV LANG       en_US.UTF-8
