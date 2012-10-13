hadoop-rhq-plugin
=================

RHQ Plugin for Apache Hadoop 1.0.3

Build Plugin

mvn clean package

apache-hadoop-rhq-plugin/target/apache-hadoop-plugin-0.1-SNAPSHOT.jar



Install Plugin

http://localhost:7080/coregui/#Administration/Configuration/AgentPlugins




Prerequisites

You have to enable hadoop jmx metrics first.

Edit two files in conf dir as below.

conf/hadoop-env.sh

export JMX_OPTS="-Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.port"

export HADOOP_NAMENODE_OPTS="$JMX_OPTS=18004 $HADOOP_NAMENODE_OPTS"

export HADOOP_SECONDARYNAMENODE_OPTS="$JMX_OPTS=18005 $HADOOP_SECONDARYNAMENODE_OPTS"

export HADOOP_DATANODE_OPTS="$JMX_OPTS=18006 $HADOOP_DATANODE_OPTS"

export HADOOP_BALANCER_OPTS="$JMX_OPTS=18007 $HADOOP_BALANCER_OPTS"

export HADOOP_JOBTRACKER_OPTS="$JMX_OPTS=18008 $HADOOP_JOBTRACKER_OPTS"

export HADOOP_TASKTRACKER_OPTS="$JMX_OPTS=18009 $HADOOP_TASKTRACKER_OPTS"


conf/hadoop-metrics.properties


dfs.class=org.apache.hadoop.metrics.spi.NullContextWithUpdateThread

dfs.period=10      

mapred.class=org.apache.hadoop.metrics.spi.NullContextWithUpdateThread

mapred.period=10 

jvm.class=org.apache.hadoop.metrics.spi.NullContextWithUpdateThread

jvm.period=10 

rpc.class=org.apache.hadoop.metrics.spi.NullContextWithUpdateThread

rpc.period=10



Check enabled

http://namenode:50070/jmx

http://namenode:50070/jmx?qry=Hadoop:service=NameNode,name=NameNodeInfo