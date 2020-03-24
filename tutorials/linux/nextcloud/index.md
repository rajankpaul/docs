---
layout: default
title: NextCloud
---

*   Something

```
sudo apt install nginx -y
sudo apt install mariadb-server python-mysqldb -y

sudo mysql_secure_installation
sudo mysql -u root -p

CREATE DATABASE nextcloud;
CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL ON `nextcloud`.* TO 'nextcloud'@'localhost';
FLUSH PRIVILEGES;

sudo apt install php7.3-fpm php7.3-mbstring php7.3-mysql php7.3-curl php7.3-gd php7.3-curl php7.3-zip php7.3-xml -y

sudo systemctl enable nginx.service
sudo systemctl enable php7.3-fpm
sudo systemctl enable mariadb-server

index index.php index.html index.htm;

location ~ \.php$ {
               include snippets/fastcgi-php.conf;
               fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
        }

sudo wget https://download.nextcloud.com/server/releases/nextcloud-18.0.2.zip
cd /var/www/html/nextcloud
sudo chown www-data:www-data config apps
```

[back](../)
