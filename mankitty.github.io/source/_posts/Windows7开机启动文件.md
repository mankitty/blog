# Windows7设置进程或者脚本为开机启动

标签（空格分隔）： Windows卡机启动

---

## Windows组策略刷新
1. 运行/控制台—>regedit打开注册表
2. CURRENT_USER
计算机\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run\Service
3. LOCAL_MACHINE
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\Service
4. 示例
"C:\Program Files\Windows\abc.exe > NUL" /start,如果启动的脚本或者二进制会有输出，可以在启动向后面加 "> NUL"

