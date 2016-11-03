---
title: 管理node和npm版本
date: 2016-11-03 17:00:05
tags:
  - node
  - npm
---

# node的升级
node的版本管理工具有两种，分别是n和nvm，可以对node无痛升级，其中n比较简单，简单介绍一下,**n模块现在不支持windows系统，fuck**
## 安装
``` bash
  $ sudo npm install -g n
```
## 使用
``` bash
  # 安装最新版本node
  $ n latest
  # 安装稳定版
  $ n stable
  # 安装指定版本
  $ n 0.10.1
  # 删除某个版本
  $ n rm 0.10.1
  # 使用指定得版本
  $ n use 0.10.1
```
# npm升级
``` bash
npm install npm -g
```
# npm安装模块
``` bash
# 强制安装，因为当你执行安装命令时，如果node_modules目录中如果已经存在该模块，就不再重新安装，即使远程仓库已经存在新版本
npm install <packagename> --f
# 查看模块版本号
npm view <packagename> versions
# 安装指定版本号
npm install <packagename>@xxx
```
