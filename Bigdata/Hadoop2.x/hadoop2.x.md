[TOC]



# 一、Hadoop2.x

## 1.1 Hadoop的优势

1. 高可靠性：Hadoop底层维护多个数据副本，所以即使Hadoop某个计算元素或存储出现故障，也不会导致数据的丢失。
2. 高扩展性：在集群间分配任务数据，可方便的扩展数以千计的节点。
3. 高效性：在MapReduce的思想下，Hadoop是并行工作的，以加快任务处理的速度。
4. 高容错性：能够自动将失败的任务重新分配。

## 1.2 Hadoop1.x和Hadoop2.x的区别

- ![hadoop1.x和2.x的区别](pictures/1/hadoop1.x和2.x的区别.png)

## 1.3 Hadoop组成

### 1.3.1 HDFS

1. NameNode：存储文件的元数据，如文件名，文件目录结构，文件属性，以及每个文件的块列表和块所在的DataNode等。
2. DataNode：在本地文件系统存储文件块数据。
3. Secondary NameNode：监控HDFS状态的辅助后台程序。

### 1.3.2 YARN

- ![yarn](pictures/1/yarn.png)

### 1.3.3 MapReduce

- ![MapReduce](pictures/1/MapReduce.png)

# 二、Hadoop运行环境搭建

1. 配置JDK环境变量

2. 将hadoop解压到module文件夹

   ```
   tar -zxvf jdk-8u144-linux-x64.tar.gz  -C /opt/module/
   ```

3. 获取hadoop目录，配置环境变量

   ```
   pwd
   vim /etc/profile
   ```

4. 在文件末尾添加：

   ```
   ##HADOOP_HOME
   export HADOOP_HOME=/opt/module/hadoop-2.7.2
   export PATH=$PATH:$HADOOP_HOME/bin
   export PATH=$PATH:$HADOOP_HOME/sbin
   ```

5. 重新加载配置文件：

   ```
   source /etc/profile
   ```

# 三、Hadoop运行模式

## 3.1 本地模式

### 3.1.1 grep案例

1. 将hadoop中etc/hadoop目录中的xml文件拷贝到input目录下

   ```
   cp etc/hadoop/*.xml input/
   ```

2. ```
   hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar grep input/ output 'dfs[a-z.]+'
   ```

### 3.1.2 WordCount案例

1. 在hadoop目录下创建wcinput目录，在wcinput目录下创建wc.input文件，并写入测试数据

   ```
   mkdir wcinput
   ```

   ```
   touch wc.input
   ```

2. 统计单词个数

   ```
   hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar wordcount wcinput/ wcoutput
   ```

## 3.2 伪分布式运行模式

1. 配置集群

   (a) 配置：hadoop-env.sh

   LInux系统中获取JDK的安装路径：

   ```sh
   echo $JAVA_HOME
   ```

   修改JAVA_HOME路径：

   ```sh
   export JAVA_HOME=/opt/module/jdk1.8.0_144
   ```


   (b) 配置：core-site.xml

   ```
   <!-- 指定HDFS中NameNode的地址 -->
   <property>
   	<name>fs.defaultFS</name>
     	<value>hdfs://ip或主机名:9000</value>
   </property>
   <!-- 指定货hadoop运行时产生文件的存储目录 -->
   <property>
   	<name>hadoop.tmp.dir</name>
     	<value>/opt/module/hadoop-2.7.2/data/tmp</value>
   </property>
   ```

   ​

   (c) 配置：hdfs-site.xml

   ```
   <!-- 指定HDFS副本的数量 -->
   <property>
   	<name>dfs.replication</name>
     	<value>1</value>
   </property>
   ```


2. 启动集群

   (a) 进入hadoop目录下

   格式化NameNode（第一次启动时格式化，以后不要总格式化）

   ```sh
   bin/hdfs namenode -format
   ```


   (b) 启动NameNode

   ```
   sbin/hadoop-daemon.sh start namenode
   ```

   (c) 启动DataNode

   ```
   sbin/hadoop-daemon.sh start datanode
   ```


3. 查看集群

   (a) 查看是否启动成功

   ```sh
   [root@xpc hadoop-2.7.2]# jps 
   1812 DataNode
   2022 Jps
   129848 NameNode
   ```

   http://ip:50070