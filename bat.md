1. 检查注册表
> reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Sangfor\EDR
2. 检查注册表中某个值
> reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Sangfor\EDR /v value
3. 删除文件夹
> rd /q /s
4. 判断文件存在
> if exist "Updater.exe" (echo ok ) else (echo err)
5. 根据进程名杀进程
> taskkill /im name