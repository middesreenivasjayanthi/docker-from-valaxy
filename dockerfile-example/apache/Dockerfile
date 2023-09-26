FROM amazonlinux

RUN yum install httpd -y && \
    yum install git -y

RUN mkdir /root/.ssh

COPY ./id_rsa /root/.ssh/id_rsa

RUN chmod -R 700 /root/.ssh  && \
    chown -R root:root /root/.ssh && \
    chmod 600 /root/.ssh/id_rsa && \
    ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts

RUN git clone git@bitbucket.org:dptrealtime/html-web-app.git /var/www/html/
CMD ["/usr/sbin/httpd", "-D","FOREGROUND"]
