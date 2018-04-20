# Procedure of build hadoop docker image

## 1. build hadoop:v1.0 image
```
# cd hadoop-v1.0
# docker build -t hadoop:v1.0 .
```

## 2. build hadoop:v2.0 image

host:

```
# docker run -d hadoop:v1.0
# docker exec -it {your-container-id} /bin/bash
```

container:
```
// install java8
# sudo apt-get update \
  && sudo apt-get install -y software-properties-common \
  && sudo add-apt-repository ppa:webupd8team/java -y \
  && sudo apt-get update \
  && sudo apt-get install -y oracle-java8-installer

//config openssh
# vim /etc/ssh/sshd_config
set PermitRootLogin yes
// permit login without password
# ssh-keygen -t rsa && cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
# service ssh restart
# ssh localhost // yes

//config mysql
# vim /etc/mysql/my.cnf
//set character_set_server=utf8
# mysql -u root -p //add hive db
mysql> create database hive;
mysql> grant all on *.* to hive@localhost identified by 'hive';
mysql> alter database hive character set latin1;
mysql> use mysql;
mysql> UPDATE user SET Password = PASSWORD('123456') WHERE user = 'root';
mysql> FLUSH PRIVILEGES;
mysql> exit

// config hive dir in hdfs
# /usr/local/hadoop/bin/hdfs namenode -format
# /usr/local/hadoop/sbin/start-dfs.sh
# /usr/local/hadoop/sbin/start-yarn.sh
# /usr/local/hadoop/bin/hadoop fs -mkdir /tmp
# /usr/local/hadoop/bin/hadoop fs -mkdir /user
# /usr/local/hadoop/bin/hadoop fs -mkdir /user/hive
# /usr/local/hadoop/bin/hadoop fs -mkdir /user/hive/warehouse
# /usr/local/hadoop/bin/hadoop fs -chmod g+w /tmp
# /usr/local/hadoop/bin/hadoop fs -chmod g+w /user/hive/warehouse

// config sunpinyin simplify input

// start firefox once

# rm -f /tmp/.X0*
# exit
```

host:
```
# docker commit {your-containerid} hadoop:v2.0
```

ok, enjoy your study!
