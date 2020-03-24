---
layout: default
title: NextCloud
---

*   Something

```
sudo apt install apache2 -y
sudo apt install mariadb-server python-mysqldb -y

sudo mysql_secure_installation
sudo mysql -u root -p

CREATE DATABASE nextcloud;
CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL ON `nextcloud`.* TO 'nextcloud'@'localhost';
FLUSH PRIVILEGES;

sudo apt install php7.3 php7.3-mbstring php7.3-mysql php7.3-curl php7.3-gd php7.3-curl php7.3-zip php7.3-xml -y

sudo service apache2 restart
sudo systemctl enable apache2.service
sudo systemctl enable mariadb-server

index index.php index.html index.htm;

sudo wget -O latest.zip https://download.nextcloud.com/server/releases/nextcloud-18.0.2.zip
cd /var/www/html/nextcloud
sudo chown www-data:www-data config apps
sudo mkdir -p /var/nextcloud/data
sudo chown www-data:www-data /var/nextcloud/data
sudo chmod 750 /var/nextcloud/data

sudo vim /etc/php/7.3/apache2/php.ini
post_max_size = 0
upload_max_filesize = 0
sudo vim /var/www/html/nextcloud/config.php

sudo vim /etc/apache2/apache2.conf

<Directory /var/www/>        
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

sudo vim /etc/apache2/sites-enabled/000-default.conf
```

[back](../)
