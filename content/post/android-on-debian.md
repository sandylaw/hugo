---
title: android on debian
date: 2018-01-06 11:46:43
tags:
---

## Setting Up ADB on Linux

<https://androidonlinux.wordpress.com/2013/05/12/setting-up-adb-on-linux/>

## install

```
sudo apt install openjdk-9-jre
sudo apt install android-tools-adb android-tools-fastboot 
 
```

## useage

### 探测设备

`adb devices`

### 启动黑域
`adb -d shell sh /data/data/me.piebridge.brevent/brevent.sh`

### 推送文件

`adb push file /sdcard/ `

### 安装App

`adb install xx.apk`