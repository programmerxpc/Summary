# 一、准备工作：

1. 在/opt目录下创建两个文件夹software，module

   ```
   cd /opt
   mk dir software
   mk dir module
   ```

2. 将jdk上传至software文件夹，并解压到module文件夹中

   ```
   tar -zxvf jdk-8u144-linux-x64.tar.gz  -C /opt/module/
   ```

# 二、步骤

1. 进入jdk所在文件夹获取目录：

   ```
   cd /opt/module/jdk1.8.0_144/
   pwd
   ```

2. 配置环境变量：

   ```
   vim /etc/profile
   ```

   在文件最后输入：

   ```
   ##JAVA_HOME
   export JAVA_HOME=/opt/module/jdk1.8.0_144
   export PATH=$PATH:$JAVA_HOME/bin
   ```

3. 重新加载配置文件并测试:

   ```
   source /etc/profile
   java -version
   ```

   ​