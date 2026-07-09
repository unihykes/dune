## remote-ssh连不上
远端服务器无法访问 downloads.cursor.com，导致 Cursor Server 安装失败。
手动下载并部署。从你本地（能访问外网的机器）下载这个文件(具体版本号会变)：
https://downloads.cursor.com/production/23b9fb205fe595ea2be29da7214e19762d037fc3/linux/x64/cursor-reh-linux-x64.tar.gz
然后 scp 到远端，解压到 ~/.cursor-server/bin/linux-x64/23b9fb205fe595ea2be29da7214e19762d037fc0/ 目录下。