# docker build Dockerfile ENV
```
ENV is a pair of key and value of Dockerfile.
ENV will be in the environment for all subsequent instructions in the build stage
```
```
$ cat Dockerfile
FROM ubuntu:16.04_3rd_hadoop2

ENV HADOOP_HOME /usr/lib/hadoop/hadoop-2.8.5
ENV HADOOP_CONF $HADOOP_HOME/etc/hadoop
ENV SPARK_HOME /usr/lib/spark/spark-2.4.3-bin-hadoop2.7

RUN echo $HADOOP_HOME && echo $HADOOP_CONF && echo $SPARK_HOME
```
