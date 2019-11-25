---
title: debian9
date: 2017-12-22 03:49:53
tags:
---
## Wifi driver

`apt install hardinfo`

`mousepad /etc/apt/sources.list`

```
deb http://mirrors.ustc.edu.cn/debian/ stretch main contrib non-free
deb-src http://mirrors.ustc.edu.cn/debian/ stretch main contrib non-free
```

`apt update`

`apt install iwlwifi`


##  Sogoupinyin

visit <https://pinyin.sogou.com> download the `sogoupinyin` deb

`sudo dpkg -i sogoupinyin_2.2.0.0102_amd64.deb`

`sudo apt --fix-broken install`

* Use `.xprofile` if you are using GDM, LightDM or SDDM with Xorg.
* Use `/etc/environment` for Wayland, it will not read environment variables stored in `~/.xprofile`
* Use `.xinitrc` if you are using startx or Slim. 

```

 export GTK_IM_MODULE=fcitx
 export QT_IM_MODULE=fcitx
 export XMODIFIERS=@im=fcitx

```
* Set Userface as zh_CN

`mousepad .bash_profile`

```

export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
export LC_CTYPE=en_US.UTF-8

```

## 访问路由器共享硬盘

`sudo apt install cifs-utils`

`mkdir kindle soft GNU film TVPlay linux music 学而思`

`mousepad mountn.sh`

```

#! /bin/bash
# mount n
sudo mount.cifs //R8500-52F6/kindle kindle -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0; sudo mount.cifs //R8500-52F6/film film -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0; sudo mount.cifs //R8500-52F6/GNU GNU -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0; sudo mount.cifs //R8500-52F6/linux linux -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0; sudo mount.cifs //R8500-52F6/music music -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0; sudo mount.cifs //R8500-52F6/soft soft -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0; sudo mount.cifs //R8500-52F6/TVPlay TVPlay -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0;sudo mount.cifs //R8500-52F6/'学而思' '学而思'  -o user=sandy,password=ganghun2008,uid=1000,gid=985,rw,file_mode=0777,dir_mode=0777,vers=2.0

```

`mousepad umount.sh`

```
#! /bin/bash
# umount n
sudo umount kindle soft GNU film TVPlay linux music 学而思

```

`sudo chmod+ x mount.sh umount.sh`

`./mountn.sh`

`./umountn.sh`

