FROM amazonlinux:2 AS build
ENV PATH $PATH:/opt/maven/bin
ENV M2_HOME /opt/maven
RUN export PATH
RUN export JAVA_HOME
RUN yum install wget -y && \
    yum install gzip -y && \
    yum install tar -y && \
    yum install git -y
RUN yum install java-1.8.0-openjdk-devel -y

RUN wget https://archive.apache.org/dist/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz && \
    tar zxf apache-maven-3.8.6-bin.tar.gz && \
    mv apache-maven-3.8.6 /opt/maven

RUN mkdir /root/.ssh

COPY ./id_rsa /root/.ssh/id_rsa

RUN chmod -R 700 /root/.ssh  && \
    chown -R root:root /root/.ssh && \
    chmod 600 /root/.ssh/id_rsa && \
    ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts

RUN git clone git@bitbucket.org:dptrealtime/java-login-app.git /opt/app
WORKDIR /opt/app
RUN /opt/maven/bin/mvn package

FROM amazonlinux:2
RUN yum install wget -y && \
    yum install gzip -y && \
    yum install tar -y
RUN yum install java-1.8.0-openjdk-devel -y
RUN wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.82/bin/apache-tomcat-8.5.82.tar.gz && \
    tar zxf apache-tomcat-8.5.82.tar.gz && \
    mv apache-tomcat-8.5.82 /opt/tomcat
COPY --from=build /opt/app/target/dptweb-1.0.war /opt/tomcat/webapps/
CMD  ["/opt/tomcat/bin/catalina.sh", "run"]