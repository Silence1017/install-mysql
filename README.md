## 简介
这是安装`mysql`数据库的具体过程。

## 过程
使用`apt-get`安装`mysql`：  
先删除`mysql`：`sudo rm /var/lib/mysql/ -R`  
`sudo rm /etc/mysql/ -R`  
`sudo apt-get autoremove mysql* --purge`  
`sudo apt-get remove apparmor`  
`sudo apt-get install mysql-server mysql-common`  
登录`mysql`测试：`mysql -uroot -p+密码`  
出现问题：由于下载后`root`用户密码随机无法登录，需要设置密码。  
https://www.liangzl.com/get-article-detail-125882.html  
解决方案：使用`cat`命令查看默认用户名密码  
`sudo cat /etc/mysql/debian.cnf`   
使用默认用户名密码登录：`mysql -udebian-sys-maint -p0XRu7iGdhb6UT8Af`  
修改配置密码：（把`root`的密码填入自己设置的密码）  
`UPDATE mysql.user SET authentication_string=PASSWORD('root的密码'), PLUGIN='mysql_native_password' WHERE USER='root';`  
退出`mysql`后重启：`service mysql restart`  
登录：`mysql -uroot -p+密码`  
