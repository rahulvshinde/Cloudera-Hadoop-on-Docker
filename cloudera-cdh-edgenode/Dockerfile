#########################################################################################
# This dockerfile is derived from rshinde26/cloudera-cdh and will setup an edge node to
# works with the other cloudera containers.
# It also contains some pig/hive script and CSV test files to start with
#
#########################################################################################
FROM rshinde26/cloudera-cdh

MAINTAINER Rahul Shinde <r.shinde2007@gmail.com>

#install pig, hive, flume and scoop 
RUN yum -y install wget vim pig hive flume-ng sqoop2 spark-worker && rm -rf /var/cache/yum/*

#copy project files
RUN mkdir /dataset
RUN mkdir /dataset/small_files
RUN mkdir /dataset/script
RUN mkdir /WordCount

COPY split.py /dataset/script
COPY dataset.xml /dataset

COPY WordCount/* /WordCount

#copy test data and script
COPY cities.* /

#copy flume conf and start scripts
COPY flume/* /
RUN chmod +x /start_flume.sh

#create a staging disk to send/get data to/from the clusrer
RUN mkdir /staging

VOLUME /staging

CMD ["bash"]