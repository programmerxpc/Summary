[TOC]

#### 1. oracle出现ora-01045的解决方法

ora-01045 :user system lacks create session privilege; logon denied

原因：该用户没有创建session会话的权限

解决办法：使用系统用户登陆后，使用如下sql语句给出错用户赋权限

grant create seesion to UserName;（UserName是登录出错的用户名）

#### 2. oracle出现ora-010031

原因：权限不足

解决方法：grant connect,resource,dba to UserName;（UserName是出错的用户名）

grant all privileges to UserName





