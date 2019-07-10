FROM fushuitong/tomcat:jdk7u21-tomcat7.0.77-cronolog1.6.2-noserverxml

ENV CATALINA_HOME /usr/local/tomcat
ENV TZ=Asia/Shanghai

RUN rm -rf $CATALINA_HOME/webapps/* && \
    rm -rf $CATALINA_HOME/conf/server.xml && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone

ADD ./*.war $CATALINA_HOME/webapps
ADD ./server.xml $CATALINA_HOME/conf
