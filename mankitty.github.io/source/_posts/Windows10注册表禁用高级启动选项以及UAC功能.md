---
title: Windows10注册表禁用高级启动选项以及UAC功能
date: 2020-02-29 20:50:21
---
## 禁用UAC功能
1. 打开运行输入RegEdit.msc
2. 在注册表中找到如下的registry key
```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\System
```
3. 修改EnableLUA值
修改EnableLUA的注册表项值改为0
## 禁用用高级启动
1. 打开运行输入RegEdit.msc
2. 计算机本地策略->用户配置->管理模板->所有设置
```
找到删除"删除并组织访问关机,"重新启动","睡眠","休眠"命令，并配置为"未配置"
```