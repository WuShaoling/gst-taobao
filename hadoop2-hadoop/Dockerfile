# already installd java8, openssh-server(permit root login without password), mysql
FROM bigdata:base

# hadoop
## install hadoop
RUN wget http://mirrors.hust.edu.cn/apache/hadoop/common/hadoop-2.7.5/hadoop-2.7.5.tar.gz \
    && tar -zxvf hadoop-2.7.5.tar.gz -C /usr/local \
    && mv /usr/local/hadoop-2.7.5 /usr/local/hadoop \
    && rm -f hadoop-2.7.5.tar.gz
## config hadoop
RUN mkdir /usr/hadoop \
    && mkdir /usr/hadoop/tmp \
    && mkdir /usr/hadoop/hdfs \
    && mkdir /usr/hadoop/hdfs/data \
    && mkdir /usr/hadoop/hdfs/name
ADD hadoop-config/* /usr/local/hadoop/etc/hadoop/
RUN /usr/local/hadoop/bin/hdfs namenode -format

# install and config hive
RUN wget http://mirrors.hust.edu.cn/apache/hive/hive-1.2.2/apache-hive-1.2.2-bin.tar.gz \
    && tar -zxvf apache-hive-1.2.2-bin.tar.gz -C /usr/local \
    && mv /usr/local/apache-hive-1.2.2-bin /usr/local/hive \
    && rm -f apache-hive-1.2.2-bin.tar.gz \
    && cp /usr/local/hive/conf/hive-default.xml.template /usr/local/hive/conf/hive-default.xml \
    && echo "export HADOOP_HOME=/usr/local/hadoop" >> ~/.bashrc
ADD hive-config/* /usr/local/hive/conf/

# install mysql-connector-java
RUN wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.46.tar.gz \
    && tar -zxvf mysql-connector-java-5.1.46.tar.gz -C /usr/local \
    && mv /usr/local/mysql-connector-java-5.1.46 /usr/local/mysql-connector-java \
    && cp /usr/local/mysql-connector-java/mysql-connector-java-5.1.46-bin.jar /usr/local/hive/lib \
    && rm -f mysql-connector-java-5.1.46.tar.gz

# install and config sqoop
RUN  wget http://mirrors.hust.edu.cn/apache/sqoop/1.4.7/sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz \
  && tar -zxvf sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz -C /usr/local \
  && mv /usr/local/sqoop-1.4.7.bin__hadoop-2.6.0 /usr/local/sqoop \
  && rm -f sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz \
  && cp /usr/local/mysql-connector-java/mysql-connector-java-5.1.46-bin.jar /usr/local/sqoop/lib
ADD sqoop-config/* /usr/local/sqoop/conf

# install and config spark
RUN  wget http://mirrors.hust.edu.cn/apache/spark/spark-2.3.0/spark-2.3.0-bin-hadoop2.7.tgz \
  && tar -zxvf spark-2.3.0-bin-hadoop2.7.tgz -C /usr/local \
  && mv /usr/local/spark-2.3.0-bin-hadoop2.7 /usr/local/spark \
  && rm -f spark-2.3.0-bin-hadoop2.7.tgz \
  && cp /usr/local/spark/conf/slaves.template /usr/local/spark/conf/slaves \
  && cp /usr/local/mysql-connector-java/mysql-connector-java-5.1.46-bin.jar /usr/local/spark/jars
ADD spark-config/* /usr/local/spark/conf

# install eclipse for java ee
RUN  wget https://mirrors.shuosc.org/eclipse/technology/epp/downloads/release/oxygen/3a/eclipse-jee-oxygen-3a-linux-gtk-x86_64.tar.gz \
  && tar -zxvf eclipse-jee-oxygen-3a-linux-gtk-x86_64.tar.gz -C /usr/local \
  && rm -f eclipse-jee-oxygen-3a-linux-gtk-x86_64.tar.gz

# install tomcat
RUN  wget http://mirrors.hust.edu.cn/apache/tomcat/tomcat-8/v8.0.51/bin/apache-tomcat-8.0.51.tar.gz \
  && tar zxvf apache-tomcat-8.0.51.tar.gz -C /usr/local \
  && mv /usr/local/apache-tomcat-8.0.51 /usr/local/tomcat \
  && rm -rf apache-tomcat-8.0.51.tar.gz
