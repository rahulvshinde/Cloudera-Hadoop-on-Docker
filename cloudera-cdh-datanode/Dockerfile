#######################################################################################################################
# This dockerfile is derived from rshinde26/cloudera-cdh and will setup an HDFS datanode
#
# The datanode will expose it's 50020, 50075 and 8042 ports, to use it, you first need to start a namenode
# (using rshinde26/cloudera-hdfs-namenode) and make sure the netword stack is OK so that the namenode and datanode
# can communicate together
#######################################################################################################################
FROM rshinde26/cloudera-cdh

MAINTAINER Rahul Shinde <r.shinde2007@gmail.com>

#init datanode directory
RUN mkdir -p /hdfs/data

#setup supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

#expose port
EXPOSE 50020 50075 8042

#define HDFS volume to enable to persist datanode data (hdfs files) between restart
VOLUME /hdfs

#start the supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
