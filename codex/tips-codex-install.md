# 安装配置

## windows离线安装codex
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

## 安装后看不到remote-ssh
在~/codex/config.toml中添加:
[features]
remote_connections = true


## remote-ssh连不上
检查 SELinux 上下文, CentOS/RHEL 下 SELinux 经常会阻止 sshd 读取用户 home 目录中的文件,
如果输出的 SELinux 标签不是 ssh_home_t，那就是 SELinux 的问题
ls -laZ ~/.ssh/
修复标签:
chcon -R -t user_home_t ~/.ssh


# 在远程主机上安装并验证 Codex
该应用程序通过 SSH 使用远程用户的登录 shell 启动远程 Codex 应用服务器。
请确保该codex命令在远程主机的PATH该 shell 中可用。

离线包下载页面:
https://github.com/openai/codex/releases
找到
codex-package-x86_64-unknown-linux-musl.tar.gz
或者
codex-package-aarch64-unknown-linux-musl.tar.gz


解压后
chmod +x xxx/bin/codex
ln -sfn xxx/bin/codex ~/.local/bin/codex

补充:
据说也可以这么装:
npm install -g @openai/codex