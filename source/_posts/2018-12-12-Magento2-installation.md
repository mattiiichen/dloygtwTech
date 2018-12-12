---
title: Magento 2 安裝
comments: false
toc: true
date: 2018-12-12 11:26:52
tags:
  - Magento 2
categories:
  - Magento
photos:
  - 2018/12/12/Magento2-installation/magento2-featured.png
---

Magento 2 的安裝，以 PHP, Mariadb, Nginx 為 Base。

<!-- more -->

#### 安裝php7.0 

1. 開啟  /usr/local/etc/php/7.0/php-fpm.d/www.conf
    * 找到user和group 改成自己的名字，例如：mattchen
    * 下方的 listen = /tem/php7.0-fpm.sock
    * 之後 cd .. 回上層
    * vi conf.d/ext-opcache.ini     這裡可找到 opcache.revalidate_freq
    * 參考：[PHP核心開發者告訴你PHP 7 的五大效能密技](https://www.ithome.com.tw/news/101602)


{% codeblock opcache的檔案 %}
[opcache]
zend_extension="/usr/local/opt/php@7.0/lib/php/20151012/opcache.so"
opcache.revalidate_freq=0  ==> 貼在這
{% endcodeblock %}

* brew service start php@7.0.  =>成功啟動
* 或是查詢 brew service list  看看清單
* brew install nginx.   安裝nginx
* cd /etc/nginx
* vi /usr/local/etc/nginx/nginx.conf
* 將user 改成自己的名字，例如：mattchen  wheel改成staff*(重要)應該在第二行
* 第36行左右的server 裡的listen 8080 改成 80
* cd servers/
* vi magento2       新增一個檔案
* 再找到這裡複製貼上，就是下面的code
把下面的路徑改正確

{% codeblock %}
upstream fastcgi_backend {
     server unix:/tmp/php7.0-fpm.sock;
 }
server {

     listen 80;
     server_name magento2.localhost;
     set $MAGE_ROOT /Users/mattchen/project/magento2;     #沒有的話記得新增資料夾 project
     include User/mattchen/project/magento2/nginx.conf.sample;
 }
{% endcodeblock %}



* 切換到在家目錄裡的project/tmp 
* cd /usr/local/bin
* 到 Composer  


* php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');”    #copy&paste 執行這行
* 再到 composer裡的gettingstart.  選mac install
* php composer-setup.php --install-dir=/usr/local/bin --filename=composer
* 再打composer 會有指令集出現
    * cd /user/local/etc/php/7.0
    * vi php.ini   把memory_limit = 2G.   還有  max_execution_time =1800
    * 把 zlib.output_compression = on
    * brew services restart php
    * /usr/local/Celler/php\@7.0/7.0.32/bin/php /usr/local/bin/composer create-project --repository=https://repo.magento.com/ magento/project-community-edition=2.2.3 magento2     接著開始下載安裝
    * https://devdocs.magento.com/guides/v2.3/install-gde/composer.html
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . // Ubuntu
chmod u+x bin/magento

{% codeblock %}
將下面改成自己的
/usr/local/Celler/php\@7.0/7.0.32/bin/php bin/magento setup:install \
--base-url=http://magento2.localhost \
--db-host=localhost \
--db-name=magento2 \
--db-user=root \
--db-password=rootpaswd \
--backend-frontname=admin \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=matt.chen@acer.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1
{% endcodeblock %}

* sudo vi /etc/hosts
* 加入 127.0.0.1    magento2.localhost
* ping magento2.localhost    看有沒有ping到
* brew services start nginx. 打開local 會發現還是連不上
* cd /usr/local/etc/nginx/servers/
* vi magento2    好像不用改
* cd ~/project/magento2
* vi  php.ini.sample 也不用改
* vi php.ini.sample   
* 找到 include /urs/loca/etcl/fastcgi_params;
* 下面還有一個也記得改，都把 fastcgi_params改成正確路徑，找全部的檔案
* brew services restart nginx
* brew services list
* fedora nginx php-fpm    => 用google 搜會找到下面的

{% codeblock %}
    server {
        server_name testsite.local;
        access_log /tmp/test_access.log;
        error_log /tmp/test_error.log;
        root /Users/mattchen/project/test;

        location / {
            index index.html index.htm index.php;
        }

        location ~ \.php$ {
            include /usr/local/etc/nginx/fastcgi_params;
            fastcgi_pass  unix:tm[/php7.0-fpm.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
    }
{% endcodeblock %}

* brew services restart
* /usr/local/etc/nginx/nginx.conf  => 找到 listen 改成 80 port
* sudo lsof -n -i:80  | grep LISTENN   查詢現在所用的埠號
* 未完成…要重新安裝看看，自己run 一遍