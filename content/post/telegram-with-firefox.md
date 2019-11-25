---
title: telegram with firefox
date: 2017-12-17 18:48:48
tags: 
 - telegram
 - firefox
---

## firefox打不开tg协议

`Firefox 不知道如何打开这个地址，因为协议 (tg) 未与任何程序关联，或者不允许在这种情况下进行。`

<https://github.com/telegramlist/telegramlist>

## 解决办法

- Go to `about:config`
- Add new boolean(布尔) named `network.protocol-handler.expose.tg` and set it to `false`
- Create the link by opening an empty tab and typing the following in the location bar在新的标签地址栏打开这条命令`data:text/html,<a href="tg://resolve?domain=Bold">Link</a>`
- Click on Link and Firefox should ask you to choose the program选择tg
- Check the box in order to remember it for future use选择一直用tg打开

