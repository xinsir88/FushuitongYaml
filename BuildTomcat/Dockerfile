FROM ubuntu:14.04.5

ENV TOMCAT_HOME /usr/local/tomcat
ENV SERVER_XML /configfile
ENV JAVA_HOME /opt/jdk1.7.0_21
ENV JRE_HOME $JAVA_HOME/jre
ENV JAVA_BIN $JAVA_HOME/bin
ENV CLASSPATH $CLASSPATH:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
ENV PATH $TOMCAT_HOME/bin:$JAVA_BIN:$JAVA_HOME/jre/bin:$PATH:$HOME/bin

ADD jdk-7u21-linux-x64.tar.gz /opt
ADD apache-tomcat-7.0.77.tar.gz  /usr/local

RUN mv /usr/local/apache-tomcat-7.0.77 /usr/local/tomcat && chmod a+x /usr/local/tomcat/bin/*.sh

ADD ./catalina.sh $TOMCAT_HOME/bin/
ADD ./cronolog-1.6.2.tar.gz /opt/
ADD ./start.sh $TOMCAT_HOME/bin/

WORKDIR /opt/cronolog-1.6.2
RUN apt-get update -y && apt-get install gcc make -y && \
    ./configure && make && make install && chmod a+x $TOMCAT_HOME/bin/start.sh  $TOMCAT_HOME/bin/catalina.sh && \
    rm -rf $TOMCAT_HOME/webapps/* && rm -rf $TOMCAT_HOME/conf/server.xml

EXPOSE 8080
ENTRYPOINT ["/bin/sh", "/usr/local/tomcat/bin/start.sh"]
