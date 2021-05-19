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

