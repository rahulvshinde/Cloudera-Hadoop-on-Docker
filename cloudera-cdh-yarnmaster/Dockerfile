#######################################################################################################################
# This dockerfile is derived from rshinde26/cloudera-cdh and will setup a  Yarn ressource manager and an MapReducev2 HistoryServer
#
# The ressource manager will expose it's 8032 port, to use it, you first need to start a datanode 
# (using rshinde26/cloudera-hdfs-datanode) and make sure the netword stack is OK so that the ressource manager and datanode 
# can communicate together
#
# The container will use supervisor to start both components.
#######################################################################################################################
FROM rshinde26/cloudera-cdh

MAINTAINER Rahul Shinde <r.shinde2007@gmail.com>

#setup supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

#expose ressourcemanager port
EXPOSE 8032 8080

#start the supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
