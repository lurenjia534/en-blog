---
title: "Arch config Redis"
date: 2024-05-09
categories: ["Arch","Linux"]
tags: ["Arch","Linux"]
---

## Arch install Redis

```shell
sudo pacman -Syu # update system
```

```shell
sudo pacman -S redis # install redis
```

## config Redis Service

Dot not start redis service after install, we need to config redis service first.

redis default config file is located at `/etc/redis/redis.conf`,but we dot not use this file, we use `/etc/redis/minimal-redis.conf` instead.

file demo `/etc/redis/minimal-redis.conf`:

the file is a minimal configuration file for redis, we can use this file to start redis service.

```shell
# Redis minimal configuration file

# Specify the Redis server port
port 6379

# Specify the directory for storing data files
dir /var/lib/redis

# Specify the log file (empty string for standard output)
logfile ""

# Bind to localhost to accept connections only from the local machine
bind 127.0.0.1

# Set the database number (default is 16)
databases 16

# Disable protected mode to allow connections only from localhost
protected-mode yes

```

Arch Redis start service file is located at `/usr/lib/systemd/system/redis.service`

the config file use Chinese locale, so we need to add locale config to the service file.

```shell
[Unit]
Description=Advanced key-value store
After=network.target

[Service]
Environment="LANG=zh_CN.UTF-8"  # Fix Failed to configure LOCALE for invalid locale name
Environment="LC_ALL=zh_CN.UTF-8" # Fix Failed to configure LOCALE for invalid locale name
Type=notify
User=redis
Group=redis
ExecStart=/usr/bin/redis-server /etc/redis/minimal-redis.conf --supervised systemd # Change the configuration file to start Redis with our set minimal configuration file.
TimeoutStartSec=60
TimeoutStopSec=60
CapabilityBoundingSet=
PrivateTmp=true
PrivateDevices=true
ProtectSystem=full
ProtectHome=true
NoNewPrivileges=true
RuntimeDirectory=redis
RuntimeDirectoryMode=755
LimitNOFILE=10032

[Install]
WantedBy=multi-user.target
```

## Set Redis service privilege (maybe not necessary)

```shell
sudo mkdir -p /var/run/redis
sudo chown redis:redis /var/run/redis
sudo chmod 755 /var/run/redis
```

## Start Redis service

```shell
sudo systemctl start redis # start redis service
```

```shell
sudo systemctl enable redis # enable redis service
```

## Check Redis service status

```shell
sudo systemctl status redis # active (running)
```

## Test Redis service connection

```shell
redis-cli ping # PONG
```
