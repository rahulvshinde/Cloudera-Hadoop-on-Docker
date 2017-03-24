###########################################################################################
# This dockerfile is derived from rshinde26/cloudera-cdh and will setup an HDFS namenode 
# and an HDFS secondarynamenode
#
# The namenode will expose it's 8020 port, to use it, you first need to start a datanode 
# (using rshinde26/cloudera-hdfs-datanode) and make sure the netword stack is OK 
# so that the namenode and datanode can communicate together
#
# The container will use supervisor to start both the namenode and the secondarynamenode.
###########################################################################################
FROM rshinde26/cloudera-cdh

MAINTAINER Rahul Shinde <r.shinde2007@gmail.com>

#init namenode directory
RUN mkdir -p /hdfs/nm

#install the namenode stuff
RUN yum -y install hadoop-hdfs-namenode && rm -rf /var/cache/yum/*

#format the namenode
RUN hdfs namenode -format

#setup supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

#expose namenode port
EXPOSE 8020

#define HDFS volume to enable to persist namenode fsimage between restart
VOLUME /hdfs

#start the supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
