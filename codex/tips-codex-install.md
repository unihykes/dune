# 安装配置

## 离线安装codex
打开微软商城，搜索 Codex，复制地址栏里的链接。
https://apps.microsoft.com/detail/9PLM9XGG6VKS?hl=neutral&gl=CN&ocid=pdpshare
打开
https://store.rg-adguard.net/
把链接粘贴进去解析，找到 .msix 文件下载。
文件名类似OpenAI.Codex_26.506.3741.0_x64__2p2nqsd0c76g0.Msix，版本号会更新。
从开始菜单打开 PowerShell
cd 到下载目录
Add-AppxPackage .\你下载的文件名.Msix


## 离线安装后,点击codex没反应
```bat
没有C:\Program Files\WindowsApps 目录访问权限，我执行了两条命令，
takeown /f "C:\Program Files\WindowsApps" /r /d y
icacls "C:\Program Files\WindowsApps" /grant "Administrators:F" /t
找到codex可执行文件将其设置为桌面快捷方式，就可以使用了
C:\Program Files\WindowsApps\OpenAI.Codex_xxxxx\app\Codex.exe

但是可能有风险
```