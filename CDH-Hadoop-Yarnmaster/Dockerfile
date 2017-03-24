FROM rshinde26/cdh-hadoop-base

MAINTAINER Rahul Shinde <r.shinde2007@gmail.com>
LABEL description="Cloudera Hadoop 5.9 Yarnmaster Docker Image"

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
EXPOSE 8032 8080
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
