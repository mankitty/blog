---
title: Linux生成core文件、core文件路径设置
date: 2020-06-04 15:27:21
---
## 设置core文件大小
1. 设置core文件大小： ulimit -c fileSize core文件超出该大小就不能生成了
2. 设置core文件无限制： ulimit -c unlimited

## 设置core文件的名称和文件路径
### 设置pid作为文件扩展名
#### 修改proc文件修改
echo "1" > /proc/sys/kernel/core_uses_pid
#### 使用sysctl命令修改
sysctl -w kernel.core_uses_pid=1 kernel.core_uses_pid = 1
```
1：添加pid作为扩展名，生成的core文件名称为core.pid
0：不添加pid作为扩展名，生成的core文件名称为core
```

### 控制core文件保存位置和文件名格式
#### 修改proc文件修改
echo "/corefile/core-%e-%p-%t" > /proc/sys/kernel/core_pattern
#### 使用sysctl命令修改
sysctl -w kernel.core_pattern=/corefile/core.%e.%p.%s.%E
```
使用上述命令可以将core文件统一生成到/corefile目录下，产生的文件名为core-命令名-pid-时间戳
以下是参数列表:
%p - insert pid into filename 添加pid(进程id)
%u - insert current uid into filename 添加当前uid(用户id)
%g - insert current gid into filename 添加当前gid(用户组id)
%s - insert signal that caused the coredump into the filename 添加导致产生core的信号
%t - insert UNIX time that the coredump occurred into filename 添加core文件生成时的unix时间
%h - insert hostname where the coredump happened into filename 添加主机名
%e - insert coredumping executable name into filename 添加导致产生core的命令名
```
## 测试是否能生成core文件
kill -s SIGSEGV $$
查看/corefile目录下是否生成了core文件