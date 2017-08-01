#windows安装centos7双系统后丢失windows启动项的简单解决方法 
windows 7、8/10 安装 *centos7*(CentOS-7-x86_64-DVD-1611.iso)双系统后，默认会将mbr改写成为grub2，而默认的centos7不识别windows 的ntfs分区，所以启动项没有windows。
可以用3条命令，即可将windows添加到grub2的启动项。
>`yum -y install epel-release`
 `yum -y install ntfs-3g`
 `grub2-mkconfig -o /boot/grub2/grub.cfg`

#文件操作
`rm -r  + 目录/文件名 #使用递归删除，好处是能看到，缺点是对于文件夹删除的话会特别的慢`
`rm -rf + 目录/文件名 #彻底删除文件夹，好处是一次性干净，缺点是如果看的不仔细误删别的文件就GG了`
`rm -ir + 目录/文件名 #交互式删除文件，好处就是每次删东西都会让你确认一下，缺点还是对于整个不要的文件就显得有些慢了`
`mkdir + 目录/文件名 #新建一个在目录下的文件名的文件`
`vi + 目录/文件名 #创建脚本`
`mv 文件名 移动目的地文件名 #移动文件`
`mv 文件名 修改后的文件名 #重命名文件`

#vim 命令
![vim命令](http://img.blog.csdn.net/20160712110935064?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

#安装谷歌浏览器
* 配置yum下载源：
在目录 /etc/yum.repos.d/ 下新建文件 google-chrome.repo, ：
`[09az@localhost ~]# cd /etc/yum.repos.d/`

`[09az@localhost yum.repos.d]# sudo vi google-chrome.repo`

* 在该文件中添加如下内容
>[google-chrome]
 name=google-chrome
 baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
 enabled=1
 gpgcheck=1
 gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub

* 执行安装命令：
`[root@localhost yum.repos.d]# yum -y install google-chrome-stable --nogpgcheck`



#安装PhpStorm 和 WebStorm

## 安装jdk

1. 
2. 配置系统环境变量，编辑`/etc/profile`添加如下内容
> vim /etc/profile 
 # 添加以下内容 
 JAVA_HOME=/usr/local/java 
 PATH=$JAVA_HOME/bin:$PATH
 CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
 export JAVA_HOME 
 export PATH
 export CLASSPATH
 
3. 使配置生效,推出编辑 并运行
`source /etc/profile `
4. 验证安装是否成功，运行
`java -version`

## 安装phpstrom
1. 把`PhpStorm-2017.1.4.tar.gz`解压到`/usr/local/phpstorm`
2. 进入`phpstorm/bin`目录，运行`phpstorm.sh`文件
> `[09az@localhost bin]$ ./phpstorm.sh`
3. 破解
 * 把 `0.0.0.0 account.jetbrains.com` 添加到`etc/hosts`文件
 * 注册码
 > CNEKJPQZEX-eyJsaWNlbnNlSWQiOiJDTkVLSlBRWkVYIiwibGljZW5zZWVOYW1lIjoibGFuIHl1IiwiYXNzaWduZWVOYW1lIjoiIiwiYXNzaWduZWVFbWFpbCI6IiIsImxpY2Vuc2VSZXN0cmljdGlvbiI6IkZvciBlZHVjYXRpb25hbCB1c2Ugb25seSIsImNoZWNrQ29uY3VycmVudFVzZSI6ZmFsc2UsInByb2R1Y3RzIjpbeyJjb2RlIjoiQUMiLCJwYWlkVXBUbyI6IjIwMTgtMDEtMzAifSx7ImNvZGUiOiJETSIsInBhaWRVcFRvIjoiMjAxOC0wMS0zMCJ9LHsiY29kZSI6IklJIiwicGFpZFVwVG8iOiIyMDE4LTAxLTMwIn0seyJjb2RlIjoiUlMwIiwicGFpZFVwVG8iOiIyMDE4LTAxLTMwIn0seyJjb2RlIjoiV1MiLCJwYWlkVXBUbyI6IjIwMTgtMDEtMzAifSx7ImNvZGUiOiJEUE4iLCJwYWlkVXBUbyI6IjIwMTgtMDEtMzAifSx7ImNvZGUiOiJSQyIsInBhaWRVcFRvIjoiMjAxOC0wMS0zMCJ9LHsiY29kZSI6IlBTIiwicGFpZFVwVG8iOiIyMDE4LTAxLTMwIn0seyJjb2RlIjoiREMiLCJwYWlkVXBUbyI6IjIwMTgtMDEtMzAifSx7ImNvZGUiOiJEQiIsInBhaWRVcFRvIjoiMjAxOC0wMS0zMCJ9LHsiY29kZSI6IlJNIiwicGFpZFVwVG8iOiIyMDE4LTAxLTMwIn0seyJjb2RlIjoiUEMiLCJwYWlkVXBUbyI6IjIwMTgtMDEtMzAifSx7ImNvZGUiOiJDTCIsInBhaWRVcFRvIjoiMjAxOC0wMS0zMCJ9XSwiaGFzaCI6IjUxOTU1OTMvMCIsImdyYWNlUGVyaW9kRGF5cyI6MCwiYXV0b1Byb2xvbmdhdGVkIjpmYWxzZSwiaXNBdXRvUHJvbG9uZ2F0ZWQiOmZhbHNlfQ==-QOxwjWvRwJz6vo6J6adC3CJ4ukQHosbPYZ94URUVFna/Rbew8xK/M5gP3kAaPh6ZDveFdtMR1UBoumq3eCwXtXM3U3ls5noB4LIr+QplVlCj2pK5uNq7g/feyNyQcHpSXtvhIOnXDBLOecB05DOsxzm0p7ulGGJoAInmHeb9mc0eYjqc4RPpUQfh6HSYBnvEnKMlLF5bz4KEtzmsvvgA55CwzwQ3gRitm5Q/wUT7AQCBdjmBfNUjKVQL6TSjSDPp56FUdEs4Aab8LqstA2DIMbxocO64rvytmcUeIwu8Mi5uq87KQP5AQMSMYb59Inbd+dmVfx5cJo3fRS4/5s3/Hg==-MIIEPjCCAiagAwIBAgIBBTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE1MTEwMjA4MjE0OFoXDTE4MTEwMTA4MjE0OFowETEPMA0GA1UEAwwGcHJvZDN5MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxcQkq+zdxlR2mmRYBPzGbUNdMN6OaXiXzxIWtMEkrJMO/5oUfQJbLLuMSMK0QHFmaI37WShyxZcfRCidwXjot4zmNBKnlyHodDij/78TmVqFl8nOeD5+07B8VEaIu7c3E1N+e1doC6wht4I4+IEmtsPAdoaj5WCQVQbrI8KeT8M9VcBIWX7fD0fhexfg3ZRt0xqwMcXGNp3DdJHiO0rCdU+Itv7EmtnSVq9jBG1usMSFvMowR25mju2JcPFp1+I4ZI+FqgR8gyG8oiNDyNEoAbsR3lOpI7grUYSvkB/xVy/VoklPCK2h0f0GJxFjnye8NT1PAywoyl7RmiAVRE/EKwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQC9WZuYgQedSuOc5TOUSrRigMw4/+wuC5EtZBfvdl4HT/8vzMW/oUlIP4YCvA0XKyBaCJ2iX+ZCDKoPfiYXiaSiH+HxAPV6J79vvouxKrWg2XV6ShFtPLP+0gPdGq3x9R3+kJbmAm8w+FOdlWqAfJrLvpzMGNeDU14YGXiZ9bVzmIQbwrBA+c/F4tlK/DV07dsNExihqFoibnqDiVNTGombaU2dDup2gwKdL81ua8EIcGNExHe82kjF4zwfadHk3bQVvbfdAwxcDy4xBjs3L4raPLU3yenSzr/OEur1+jfOxnQSmEcMXKXgrAQ9U55gwjcOFKrgOxEdek/Sk1VfOjvS+nuM4eyEruFMfaZHzoQiuw4IqgGc45ohFH0UUyjYcuFxxDSU9lMCv8qdHKm+wnPRb0l9l5vXsCBDuhAGYD6ss+Ga+aDY6f/qXZuUCEUOH3QUNbbCUlviSz6+GiRnt1kA9N2Qachl+2yBfaqUqr8h7Z2gsx5LcIf5kYNsqJ0GavXTVyWh7PYiKX4bs354ZQLUwwa/cG++2+wNWP+HtBhVxMRNTdVhSm38AknZlD+PTAsWGu9GyLmhti2EnVwGybSD2Dxmhxk3IPCkhKAK+pl0eWYGZWG3tJ9mZ7SowcXLWDFAk0lRJnKGFMTggrWjV8GYpw5bq23VmIqqDLgkNzuoog==

## 安装webstorm
破解,选择 `linsens server` 输入 `http://idea.iteblog.com/key.php`

## 安装nginx
1. 把`nginx-1.12.0.tar.gz`解压到`/usr/local/nginx-1.12.0`
2. 进入`nginx-1.12.0`
 > `#./configure`
*creating objs/Makefile这步之后，就成功啦！*
3. 开始编译
 >`#make`
 `#make install`

### 启动nginx
`[09az@localhost ~]# sudo /usr/local/nginx/sbin/nginx`
`[09az@localhost ~]# sudo /usr/local/nginx/sbin/nginx -s stop`
`[09az@localhost ~]# sudo /usr/local/nginx/sbin/nginx -s quit`
`[09az@localhost ~]# sudo /usr/local/nginx/sbin/nginx -s reload`

### 创建nginx服务第一步，添加一个新文件，nginx.service

1. `#vim /lib/systemd/system/nginx.service`
2. 内容如下
>[Unit]
Description=nginx
After=network.target
 
[Service]
Type=forking
ExecStart=/usr/local/nginx/sbin/nginx
ExecReload=/usr/local/nginx/sbin/nginx -s reload
ExecStop=/usr/local/nginx/sbin/nginx -s quit
PrivateTmp=true
 
[Install]
WantedBy=multi-user.target

3. 更改文件权限
`#chmod 745 /lib/systemd/system/nginx.service`

4. 设置开机自启动
`#systemctl enable nginx.service`

## 防火墙

停止firewall
`#systemctl stop firewalld.service`
禁止firewall开机启动
`#systemctl disable firewalld.service`
查看默认防火墙状态（关闭后显示not running，开启后显示running）
`#firewall-cmd --state`
或者设置通过ip访问
`firewall-cmd --permanent --zone=public --add-service=http`
`firewall-cmd --permanent --zone=public --add-service=https`
`firewall-dmd --reload`

## 配置iptables 
>这样配之后，局域网不能通过ip访问
首先需要安装iptables服务
`#yum install iptables-services`

编辑防火墙配置文件
`#vim /etc/sysconfig/iptables`

加入下面的几行，22是默认存在的
>-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -jACCEPT
 -A INPUT -p tcp -m state --state NEW -m tcp --dport 8080 -j ACCEPT
 -A INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT

*22端口是供ssh访问的，80，8080端口是http服务访问的，以后用到https，也需要打开443端口的访问权限。*

保存，重启iptables服务,重启防火墙使配置生效
`#systemctl restart iptables.service`

设置防火墙开机启动
`#systemctl enable iptables.service`

## ps
`#ps aux|grep 

## 安装php
1. `cd php-7.1.7`
2. 安装依赖
`yum install libxml2 libxml2-devel openssl openssl-devel bzip2 bzip2-devel libcurl libcurl-devel libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel gmp gmp-devel libmcrypt libmcrypt-devel readline readline-devel libxslt libxslt-devel`
3. 编译配置 (注意前两个选项，指定安装的位置)
./configure \
--prefix=/usr/local/php7 \
--with-config-file-path=/usr/local/php7/etc \
--enable-fpm \
--with-fpm-user=nginx  \
--with-fpm-group=nginx \
--enable-inline-optimization \
--disable-debug \
--disable-rpath \
--enable-shared  \
--enable-soap \
--with-libxml-dir \
--with-xmlrpc \
--with-openssl \
--with-mcrypt \
--with-mhash \
--with-pcre-regex \
--with-sqlite3 \
--with-zlib \
--enable-bcmath \
--with-iconv \
--with-bz2 \
--enable-calendar \
--with-curl \
--with-cdb \
--enable-dom \
--enable-exif \
--enable-fileinfo \
--enable-filter \
--with-pcre-dir \
--enable-ftp \
--with-gd \
--with-openssl-dir \
--with-jpeg-dir \
--with-png-dir \
--with-zlib-dir  \
--with-freetype-dir \
--enable-gd-native-ttf \
--enable-gd-jis-conv \
--with-gettext \
--with-gmp \
--with-mhash \
--enable-json \
--enable-mbstring \
--enable-mbregex \
--enable-mbregex-backtrack \
--with-libmbfl \
--with-onig \
--enable-pdo \
--with-mysqli=mysqlnd \
--with-pdo-mysql=mysqlnd \
--with-zlib-dir \
--with-pdo-sqlite \
--with-readline \
--enable-session \
--enable-shmop \
--enable-simplexml \
--enable-sockets  \
--enable-sysvmsg \
--enable-sysvsem \
--enable-sysvshm \
--enable-wddx \
--with-libxml-dir \
--with-xsl \
--enable-zip \
--enable-mysqlnd-compression-support \
--with-pear \
--enable-fastcgi \
--enable-opcache

4. 正式安装
` make && make install`

5. 配置环境变量
 * `vim /etc/profile`
    在末尾追加
 * `export PATH=/usr/local/php/bin:$PATH`
    执行命令使得改动立即生效
 * `source /etc/profile`

6. 配置php-fpm  需要在安装软件包目录（注意路径）
cp php.ini-production /etc/php.ini
cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm
chmod +x /etc/init.d/php-fpm

7. 启动php-fpm
/etc/init.d/php-fpm start

# 安装mariadb
`[09az@localhost ~]$ sudo yum -y install mariadb*`
`[09az@localhost ~]$ systemctl start mariadb.service`
`sudo mysql_secure_installation`
`[09az@localhost ~]$ systemctl enable  mariadb.service`





 
