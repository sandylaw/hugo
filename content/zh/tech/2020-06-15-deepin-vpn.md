+++
title = "Deepin Vpn命令行连接"  # 文章标题
date = 2020-06-15T09:23:33+08:00  # 自动添加日期信息
draft = false  # 设为false可被编译为HTML，true供本地修改
tags = ["Linux"]  # 文章标签，可设置多个，用逗号隔开。Hugo会自动生成标签的子URL

+++

UOS 20 也就是deepin的商业版，升级后控制中心打不开，无法图形界面连接vpn。

```bash
$ dde-control-center 
dde-control-center: symbol lookup error: dde-control-center: undefined symbol: _ZNK7__Power28BatteryLidClosedSleepChangedEb
```



经请教LinuxToy大神，告知命令行开启方法。

## revpn 脚本

```bash
#!/bin/bash
#
# Reconnect VPN
# Time-stamp: <2020-04-24 09:08:10>
#

OPT="$1"
VPN=wh-vpn-linux-tcp

if [ "$OPT" == "rs" ]
then
    nmcli connection down "$VPN" 2>/dev/null 1>&2
fi

if nmcli connection show | grep -q 'tun0'
then
    echo VPN
else
    nmcli connection up "$VPN" 2>/dev/null 1>&2
fi

```

## 软件包降级

```bash
sudo apt-cache policy dde-control-center ##查看软件包信息，包括支持的版本号
sudo apt install dde-control-center=version_num ##指定版本号安装软件包
```

回退frameworkdbus的版本，执行以下命令：

```bash
sudo apt install libdframeworkdbus2=5.1.0.1-1
```



