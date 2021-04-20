---
title: 'pi-zero学习4: pi dashboard'
date: 2021-02-27 10:40:16
tags: pi_zero
categories:
    - coding
    - pi zero
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226100542033.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226100613016.png
comment: true
---

# pi-zero学习4: pi dashboard

实时监控树莓派的网页

项目地址：

https://github.com/spoonysonny/pi-dashboard

## 1、安装lnmp

```
sudo apt-get update
```

安装Nginx，输入下面的命令

```
sudo apt-get install -y nginx
```

完全卸载：

```
$ sudo apt-get --purge remove nginx
$ sudo apt-get autoremove
$ dpkg --get-selections | grep nginx

$ sudo apt-get --purge remove nginx-common
$ sudo apt-get install nginx
```

启动nginx服务

```
sudo service nginx restart
```

安装PHP7.0，(删去版本号)

```
sudo apt-get install -y nginx php7.0-fpm php7.0-cli php7.0-curl php7.0-gd php7.0-mcrypt php7.0-cgi php7.0-mysql php7.0-mbstring

```

>The following additional packages will be installed:
>libltdl7 libmcrypt4 libsodium23 php-common php7.1-common php7.3-cgi php7.3-cli php7.3-common php7.3-curl php7.3-fpm php7.3-gd php7.3-json
>php7.3-mysql php7.3-opcache php7.3-readline

安装完毕后启动php7.0服务

```
sudo service php7.3-fpm restart
```

安装MySQL（MariaDb），输入下面的命令

```
sudo apt-get install -y mysql-server mysql-client 
```

>Reading package lists... Done
>Building dependency tree       
>Reading state information... Done
>Package mysql-client is not available, but is referred to by another package.
>This may mean that the package is missing, has been obsoleted, or
>is only available from another source
>However the following packages replace it:
>mariadb-client-10.0

> Package mysql-server is not available, but is referred to by another package.
> This may mean that the package is missing, has been obsoleted, or
> is only available from another source
> However the following packages replace it:
>   mariadb-server-10.0

更换安装命令：

```
sudo apt-get install -y mariadb-client-10.0 mariadb-server-10.0
```

安装完毕后启动mysql服务

```
sudo service mysql restart
```

如果安装成功，可通过 http:// 树莓派IP 访问到 Nginx 的默认页。Nginx 的根目录在 /var/www/html。

![image-20210227111607009](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227111607009.png)到这里，就已经安装完毕了，下面就开始配置Nginx+PHP7+MySQL(MariaDB)了。

配置见https://blog.csdn.net/alinathz/article/details/92234300



```
git clone https://github.com/spoonysonny/pi-dashboard.git


```

进入目录

接着配置nginx

```

cd /usr/local/nginx/conf/vhost
vim dashboard.conf
```

将其中的如下内容

```
location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }
```

替换为

```
location / {
index  index.html index.htm index.php default.html default.htm default.php;
}
 
location ~\.php$ {
fastcgi_pass unix:/run/php/php7.3-fpm.sock;
#fastcgi_pass 127.0.0.1:9000;
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
include fastcgi_params;
}
```

Ctrl + O 保存再 Ctrl + X 退出。

```
sudo service nginx restart
```

执行 `mysql` 命令。

```bash
MariaDB [(none)]> use mysql;
MariaDB [mysql]> update user set plugin='mysql_native_password' where user='root';
MariaDB [mysql]> UPDATE user SET password=PASSWORD('你想要设定的密码') WHERE user='root';
MariaDB [mysql]> flush privileges;
MariaDB [mysql]> exit;
```

重启服务

```bash
service mysql restart
```

部署pi dashboard：

```bash
cd /var/www/html
sudo git clone https://github.com/nxez/pi-dashboard.git
```

![image-20210227125420430](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227125420430.png)

树莓派ip可以通过

```bash
ping raspberrypi.local
```

得知

