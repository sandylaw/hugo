---
title: minidlna
date: 2018-01-06 10:34:07
tags:
---

## Minidlna

MiniDLNA is a simple media server software, with the aim of being fully compliant with DLNA/UPnP-AV clients. 

## Install

`sudo apt install minidlna`

## Setup

### 修改默认启动用户和用户组
lance:lance是我的用户名和用户组，修改成你自己的。

`sudo gedit /etc/default/minidlna`


```
# Defaults for minidlna initscript
# sourced by /etc/init.d/minidlna
# installed at /etc/default/minidlna by the maintainer scripts

# These options can be set to modify the behavior of the minidlna init script.
# The options commented out show the default values.

# Start the daemon if set to "yes"
START_DAEMON="yes"

# Path to the configuration file
#CONFIGFILE="/etc/minidlna.conf"

# Path to the log file
#LOGFILE="/var/log/minidlna.log"

# User and group the daemon should run as
USER="lance"
GROUP="lance"

# Additional options that are passed to the daemon
DAEMON_OPTS=""
```

### 修改配置文件

`sudo gedit /etc/minidlna.conf`

```
# Specify the user name or uid to run as.
user=lance
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
#   * "PV" for pictures and video (eg. media_dir=PV,/var/lib/minidlna/digital_camera)
# media_dir=/var/lib/minidlna
media_dir=V,/media/lance/film
# Path to the directory that should hold the database and album art cache.
db_dir=/home/lance/.nas
# Path to the directory that should hold the log file.
log_dir=/home/lance/.nas
# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
friendly_name=debian
# Automatic discovery of new files in the media_dir directory.
inotify=yes
# SSDP notify interval, in seconds.
notify_interval=300

```

`mkdir ~/.nas` 存放数据库和日志的目录

## Start
`sudo service minidlna start`
`sudo service minidlna restart`
`sudo service minidlna status`
`sudo service minidlna stop`

## 定时任务

`sudo gedit /etc/crontab`

每10分钟重启服务，追加定时任务：

`*/10* * * * service minidlna force-reload;/etc/init.d/minidlna restart`

重启定时任务：

`sudo /etc/init.d/cron restart`
