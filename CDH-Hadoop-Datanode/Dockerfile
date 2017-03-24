FROM rshinde26/cdh-hadoop-base

MAINTAINER Rahul Shinde <r.shinde2007@gmail.com>
LABEL description="Cloudera Hadoop 5.9 Datanode Docker Image"

RUN mkdir -p /hdfs/data
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
EXPOSE 50020 50075 8042
VOLUME /hdfs
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
