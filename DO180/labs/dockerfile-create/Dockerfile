FROM ubi7/ubi:7.7

MAINTAINER ankit

LABEL description="A custom Apache container based on UBI 7"
ENV PORT 8080
RUN yum install -y httpd && \

yum clean all
RUN sed -ri -e "/^Listen 80/c\Listen ${PORT}" /etc/httpd/conf/httpd.conf && \

chown -R apache:apache /etc/httpd/logs/ && \

chown -R apache:apache /run/httpd/
USER apache

EXPOSE ${PORT}

COPY ./src/ /var/www/html/

CMD ["httpd", "-D", "FOREGROUND"]

