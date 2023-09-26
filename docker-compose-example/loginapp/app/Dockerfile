FROM amazonlinux
MAINTAINER PRReddy
WORKDIR /opt
ADD https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.77/bin/apache-tomcat-8.5.77.zip /opt/
RUN yum install unzip -y
RUN yum install vim -y
RUN yum install mysql -y
RUN yum install telnet -y
RUN unzip /opt/apache-tomcat-8.5.77.zip
RUN chmod +x /opt/apache-tomcat-8.5.77/bin/*
RUN amazon-linux-extras install java-openjdk11 -y
COPY ./dptweb-1.0.war /opt/apache-tomcat-8.5.77/webapps/
CMD ["/opt/apache-tomcat-8.5.77/bin/catalina.sh", "run"]
