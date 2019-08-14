FROM gongzhao1995/hadoop_ubuntu:0.8
MAINTAINER gongzhao1995
USER root
#support for Hadoop 2.6.0
#RUN curl -s http://d3kbcqa49mib13.cloudfront.net/spark-1.5.1-bin-hadoop2.6.tgz | tar -xz -C /usr/local/
RUN curl -s http://mirrors.tuna.tsinghua.edu.cn/apache/spark/spark-2.4.3/spark-2.4.3-bin-hadoop2.7.tgz  | tar -xz -C /usr/local/
RUN cd /usr/local && ln -s spark-2.4.3-bin-hadoop2.7 spark
ENV SPARK_HOME /usr/local/spark
RUN mkdir $SPARK_HOME/yarn-remote-client
ADD yarn-remote-client $SPARK_HOME/yarn-remote-client
# update boot script
COPY bootstrap.sh /etc/bootstrap.sh
RUN chown root.root /etc/bootstrap.sh
RUN chmod 700 /etc/bootstrap.sh
#RUN $HADOOP_PREFIX/bin/hdfs namenode -format -force
RUN cat /etc/hosts && $BOOTSTRAP && $HADOOP_PREFIX/bin/hdfs dfsadmin -safemode leave && ls $SPARK_HOME-2.4.3-bin-hadoop2.7 && $HADOOP_PREFIX/bin/hdfs dfs -put $SPARK_HOME-2.4.3-bin-hadoop2.7 /spark

ENV YARN_CONF_DIR $HADOOP_PREFIX/etc/hadoop
ENV PATH $PATH:$SPARK_HOME/bin:$HADOOP_PREFIX/bin



#install R
#RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
#RUN apt-get -y install r-base

ENTRYPOINT ["/etc/bootstrap.sh"]