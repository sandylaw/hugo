---
title: Kindle标注转Markdown脚本
author: V2Less
date: '2020-03-08'
slug: kindle标注转markdown脚本
categories:
  - python
tags:
  - python
---

## kindleClippingsToMarkdown

[项目地址](https://github.com/sandylaw/kindleClippingsToMarkdown)

本Python3脚本功能：将Kindle标注文件转化为Markdown文件。

Copy 自 https://github.com/duarteocarmo/my-personal-zen

原脚本不支持中文，简单改了下，现已经支持中午。

原介绍链接： https://duarteocarmo.com/misc/2020/02/25/kindle-python.html 

## 获取标注文件
用数据线，连接Kindle到电脑，访问设备下的Documents目录，复制 Kindle的标注文件 `My Clippings.txt` 到当前工作目录，比如桌面。

## 下载脚本文件

[kindleClippings_highlight_parser](https://github.com/sandylaw/kindleClippings_highlight_parser/blob/master/kindleClippings_highlight_parser.py)

## 转换

在当前工作目录打开命令行，执行：
`python kindleClippings_highlight_parser.py My Clippings.txt`

脚本将按书依次生成`.MD`文件。
