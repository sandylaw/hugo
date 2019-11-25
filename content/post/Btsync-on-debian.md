---
title: Btsync on debian
date: 2018-01-05 23:27:27
tags:
---

## Install btsync on debian

<https://www.resilio.com/blog/official-linux-packages-for-sync-now-available>

## Setup btsync

`sudo gedit /lib/systemd/system/resilio-sync.service `

```
[Unit]
Description=Resilio Sync service
Documentation=https://help.getsync.com/
After=network.target network-online.target

[Service]
Type=forking
User=rslsync
Group=rslsync
UMask=0002
Restart=on-failure
PermissionsStartOnly=true
PIDFile=/var/run/resilio-sync/sync.pid
ExecStartPre=/bin/mkdir -p /var/run/resilio-sync
ExecStartPre=/bin/chown -R rslsync:rslsync /var/run/resilio-sync
ExecStart=/usr/bin/rslsync --config /etc/resilio-sync/config.json

[Install]
WantedBy=multi-user.target
```

Replay `rslsync` with your own username and group.

```
[Unit]
Description=Resilio Sync service
Documentation=https://help.getsync.com/
After=network.target network-online.target

[Service]
Type=forking
User=lance
Group=lance
UMask=0002
Restart=on-failure
PermissionsStartOnly=true
PIDFile=/var/run/resilio-sync/sync.pid
ExecStartPre=/bin/mkdir -p /var/run/resilio-sync
ExecStartPre=/bin/chown -R lance:lance /var/run/resilio-sync
ExecStart=/usr/bin/rslsync --config /etc/resilio-sync/config.json

[Install]
WantedBy=multi-user.target
```
## Reload 

`sudo systemctl daemon-reload`


## Run btsync under user-level

`systemctl --user start resilio-sync`

`systemctl --user enable resilio-sync`

## Open the web
<http://127.0.0.1:8888/gui/>

Username: your_user_name

Password: set_a_password

## Zeotier-one

```
### install the zerotier

curl -s 'https://pgp.mit.edu/pks/lookup?op=get&search=0x1657198823E52A61' | gpg --import && \
if z=$(curl -s 'https://install.zerotier.com/' | gpg); then echo "$z" | sudo bash; fi

```
`sudo apt update`

`sudo apt install zerotier-one`

### set
* Join the network of the <bookfere.com>  `17d709436c2e5dc2`or btsync `446b538c9d8ca1d3` 
```
sudo zerotier-cli join 446b538c9d8ca1d3
sudo sudo zerotier-cli set 446b538c9d8ca1d3 allowGlobal=true
sudo zerotier-cli set 446b538c9d8ca1d3 allowDefault=true
```
* Test

`sudo zerotier-cli listnetworks`

### set the define host

然后输入书伴分享的密钥` BB63I5PBPBFDELAPXI6NTF47IPNZQAAJZ`添加同步。鼠标悬浮到这条同步，点击出现在右边的“…”按钮，在弹出的菜单中点击“偏好设定…”，仅勾选“搜索 DHT 网络”和“使用预定义主机”，其它的全部取消勾选。最后在预定义主机中增加如下所示的 IP 和端口：
`172.23.156.207:57842`

* Test if you join the bookfere net

`sudo apt install net-tools`

`ping 172.23.156.207`

`sudo ifconfig`

`sudo zerotier-cli listpeers`

`zerotier-cli listnetworks`


**ok**





