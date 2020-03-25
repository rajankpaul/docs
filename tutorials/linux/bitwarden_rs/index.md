---
layout: default
title: Bitwarden_rs 
---

*   Something

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
sudo apt install openssl pkg-config libssl-dev
sudo apt install mariadb-server libmariadb-dev-compat libmariadb-dev

# download bitwarden_rs source code and web-vault binary from github
# https://github.com/dani-garcia/bw_web_builds/releases

cargo build --features mysql --release

sudo mysql_secure_installation
sudo mysql -u root -p
CREATE DATABASE bitwarden_rs;
CREATE USER 'bitwarden_rs'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALTER, CREATE, DELETE, DROP, INDEX, INSERT, SELECT, UPDATE ON `bitwarden_rs`.* TO 'bitwarden_rs'@'localhost';
FLUSH PRIVILEGES;
# set the sql environment variable to mysql://dbuser:yourpassword@192.168.1.10:3306/bitwarden
# ENABLE_DB_WAL=false
# SHOW_PASSWORD_HINT=false
# WEBSOCKET_ENABLED=true
# INVITATIONS_ALLOWED=false
# DATA_FOLDER=/var/lib/bitwarden_rs/data
# WEB_VAULT=/var/lib/bitwarden_rs/web_vault

sudo mkdir /var/lib/bitwarden_rs
sudo mkdir -p /home/pi/bitwarden_rs/data
sudo mv web_vault /home/pi/bitwarden_rs
sudo vim /etc/fstab
/home/pi/bitwarden_rs/data/ /var/lib/bitwarden_rs/data none defaults,bind 0 0
/home/pi/bitwarden_rs/web_vault/ /var/lib/bitwarden_rs/web_vault none defaults,bind 0 0
sudo cp bitwarden_rs /usr/bin/bitwarden_rs
sudo cp template.env /etc/bitwarden_rs.env
en

```
sudo vim /etc/systemd/system/bitwarden_rs.service
```
[Unit]
Description=Bitwarden Server (Rust Edition)
Documentation=https://github.com/dani-garcia/bitwarden_rs
# If you use a database like mariadb,mysql or postgresql, 
# you have to add them like the following and uncomment them 
# by removing the `# ` before it. This makes sure that your 
# database server is started before bitwarden_rs ("After") and has 
# started successfully before starting bitwarden_rs ("Requires").

# Only sqlite
# After=network.target

# MariaDB
After=network.target mariadb.service
Requires=mariadb.service

# Mysql
# After=network.target mysqld.service
# Requires=mysqld.service

# PostgreSQL
# After=network.target postgresql.service
# Requires=postgresql.service


[Service]
# The user/group bitwarden_rs is run under. the working directory (see below) should allow write and read access to this user/group
User=ubuntu
Group=ubuntu
# The location of the .env file for configuration
EnvironmentFile=/etc/bitwarden_rs.env
# The location of the compiled binary
ExecStart=/usr/bin/bitwarden_rs
# Set reasonable connection and process limits
LimitNOFILE=1048576
LimitNPROC=64
# Isolate bitwarden_rs from the rest of the system
PrivateTmp=true
PrivateDevices=true
ProtectHome=true
ProtectSystem=strict
# Only allow writes to the following directory and set it to the working directory (user and password data are stored here)
WorkingDirectory=/var/lib/bitwarden_rs
ReadWriteDirectories=/var/lib/bitwarden_rs
# Allow bitwarden_rs to bind ports in the range of 0-1024
AmbientCapabilities=CAP_NET_BIND_SERVICE

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl daemon-reload
sudo systemctl start bitwarden_rs.service
sudo systemctl enable bitwarden_rs.service
sudo ufw allow 80
sudo ufw allow 3012

# SIGNUPS_ALLOWED=false
```

[back](../)
