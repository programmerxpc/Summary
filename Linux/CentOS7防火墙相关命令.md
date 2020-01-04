1. 查看防火墙状态：

​        `systemctl status firewalld`  

2. 开启防火墙：

    `systemctl start firewalld`  

3. 关闭防火墙：

    `systemctl stop firewalld`  

4. 查看某一端口是否开启：

   `firewall-cmd --query-port=3306/tcp  # 查看3306端口是否开启`  

5. 开启某一端口：

   ```
   firewall-cmd --zone=public --add-port=3306/tcp --permanent  # 开启3306端口
   firewall-cmd --reload  # 重启防火墙  
   ```
   ​


