FROM cloudwarelabs/xfce4-pulsar-ide:latest

# install some tools
RUN apt-get update \
    && apt-get install -y gedit \
    && apt-get install -y unzip \
    && apt-get install -y vim \
    && apt-get install -y firefox \
    && apt-get install -y fcitx fcitx-sunpinyin \
    && rm -f /usr/local/bin/pulsar

RUN ls /etc/my* > /root/a.txt

# set ENV
ENV JAVA_HOME "/usr/lib/jvm/java-8-oracle"
ENV HADOOP_HOME "/usr/local/hadoop"
ENV HADOOP_MAPRED_HOME "${HADOOP_HOME}"
ENV HADOOP_COMMON_HOME "${HADOOP_HOME}"
ENV HADOOP_HDFS_HOME "${HADOOP_HOME}"
ENV YARN_HOME "${HADOOP_HOME}"
ENV HBASE_HOME "/usr/local/hbase"
ENV HIVE_HOME "/usr/local/hive"
ENV CLASSPATH "$CLASSPATH:${HADOOP_HOME}/lib/*:${HIVE_HOME}/lib/*:."
ENV PATH "$PATH:${HADOOP_HOME}/sbin:${HADOOP_HOME}/bin:${HBASE_HOME}/bin:${HIVE_HOME}/bin"

RUN ls /etc/my* > /root/b.txt

# install and config hadoop
RUN wget http://mirrors.shu.edu.cn/apache/hadoop/common/hadoop-2.7.6/hadoop-2.7.6.tar.gz \
    && tar -zxvf hadoop-2.7.6.tar.gz -C /usr/local \
    && mv /usr/local/hadoop-2.7.6 /usr/local/hadoop \
    && rm -f hadoop-2.7.6.tar.gz
RUN mkdir /usr/hadoop \
    && mkdir /usr/hadoop/tmp \
    && mkdir /usr/hadoop/hdfs \
    && mkdir /usr/hadoop/hdfs/data \
    && mkdir /usr/hadoop/hdfs/name
ADD hadoop-config/* /usr/local/hadoop/etc/hadoop/

RUN ls /etc/my* > /root/c.txt

# install and config hive
RUN wget http://mirrors.shu.edu.cn/apache/hive/hive-1.2.2/apache-hive-1.2.2-bin.tar.gz \
    && tar -zxvf apache-hive-1.2.2-bin.tar.gz -C /usr/local \
    && mv /usr/local/apache-hive-1.2.2-bin /usr/local/hive \
    && rm -f apache-hive-1.2.2-bin.tar.gz \
    && cp /usr/local/hive/conf/hive-default.xml.template /usr/local/hive/conf/hive-default.xml \
    && echo "export HADOOP_HOME=/usr/local/hadoop" >> ~/.bashrc
ADD hive-config/* /usr/local/hive/conf/
ADD hivejars /usr/local/hivejars/

RUN ls /etc/my* > /root/d.txt

# install mysql-connector-java
RUN wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.46.tar.gz \
    && tar -zxvf mysql-connector-java-5.1.46.tar.gz -C /usr/local \
    && mv /usr/local/mysql-connector-java-5.1.46 /usr/local/mysql-connector-java \
    && cp /usr/local/mysql-connector-java/mysql-connector-java-5.1.46-bin.jar /usr/local/hive/lib \
    && rm -f mysql-connector-java-5.1.46.tar.gz

RUN ls /etc/my* > /root/e.txt

# install and config sqoop
RUN  wget http://mirrors.shu.edu.cn/apache/sqoop/1.4.7/sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz \
  && tar -zxvf sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz -C /usr/local \
  && mv /usr/local/sqoop-1.4.7.bin__hadoop-2.6.0 /usr/local/sqoop \
  && rm -f sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz \
  && cp /usr/local/mysql-connector-java/mysql-connector-java-5.1.46-bin.jar /usr/local/sqoop/lib
ADD sqoop-config/* /usr/local/sqoop/conf/

RUN ls /etc/my* > /root/f.txt

# install and config spark
RUN  wget http://mirrors.shu.edu.cn/apache/spark/spark-2.3.0/spark-2.3.0-bin-hadoop2.7.tgz \
  && tar -zxvf spark-2.3.0-bin-hadoop2.7.tgz -C /usr/local \
  && mv /usr/local/spark-2.3.0-bin-hadoop2.7 /usr/local/spark \
  && rm -f spark-2.3.0-bin-hadoop2.7.tgz \
  && cp /usr/local/spark/conf/slaves.template /usr/local/spark/conf/slaves \
  && cp /usr/local/mysql-connector-java/mysql-connector-java-5.1.46-bin.jar /usr/local/spark/jars
ADD spark-config/* /usr/local/spark/conf/

RUN ls /etc/my* > /root/g.txt

# install eclipse for javaee
RUN  wget https://mirrors.shuosc.org/eclipse/technology/epp/downloads/release/oxygen/3a/eclipse-jee-oxygen-3a-linux-gtk-x86_64.tar.gz \
  && tar -zxvf eclipse-jee-oxygen-3a-linux-gtk-x86_64.tar.gz -C /usr/local \
  && rm -f eclipse-jee-oxygen-3a-linux-gtk-x86_64.tar.gz
ADD eclipse-plugins/hadoop-eclipse-plugin-2.6.0.jar /usr/local/eclipse/plugins/

RUN ls /etc/my* > /root/h.txt

# install tomcat
RUN  wget http://mirrors.shu.edu.cn/apache/tomcat/tomcat-8/v8.0.51/bin/apache-tomcat-8.0.51.tar.gz \
  && tar zxvf apache-tomcat-8.0.51.tar.gz -C /usr/local \
  && mv /usr/local/apache-tomcat-8.0.51 /usr/local/tomcat \
  && rm -rf apache-tomcat-8.0.51.tar.gz

RUN ls /etc/my* > /root/i.txt

# install and config hbase
RUN  wget http://mirrors.shu.edu.cn/apache/hbase/stable/hbase-1.2.6-bin.tar.gz \
  && tar zxvf hbase-1.2.6-bin.tar.gz -C /usr/local \
  && mv /usr/local/hbase-1.2.6 /usr/local/hbase \
  && rm -f hbase-1.2.6-bin.tar.gz
ADD hbase-config/* /usr/local/hbase/conf/

RUN ls /etc/my* > /root/j.txt
