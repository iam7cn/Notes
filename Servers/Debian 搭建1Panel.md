### 安装Debian 12后

```sudo apt update && sudo apt upgrade -y```

更新源

```nano /etc/apt/sources.list```

```
deb https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib
deb-src https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib
deb https://mirrors.aliyun.com/debian-security/ bookworm-security main
deb-src https://mirrors.aliyun.com/debian-security/ bookworm-security main
deb https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib
deb-src https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib
deb https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib
deb-src https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib
```

ssh 不方便编辑可以 新建sources.list放到个人目录中
执行命令

``` cp /home/xxx/sources.list /etc/apt/ ```

### Linux给用户添加sudo权限

使用命令```sudo usermod -a -G sudo username```，其中username是你的用户名。


### Debian安装1Panel

```curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && bash quick_start.sh```


```
[1Panel Log]:
[1Panel Log]: =================感谢您的耐心等待，安装已经完成==================
[1Panel Log]:
[1Panel Log]: 请用浏览器访问面板:
[1Panel Log]: 外网地址: http://221.131.229.54:19870/c035de27f0
[1Panel Log]: 内网地址: http://192.168.73.2:19870/c035de27f0
[1Panel Log]: 面板用户: shenweb
[1Panel Log]: 面板密码: SCM@123abc
[1Panel Log]:
[1Panel Log]: 项目官网: https://1panel.cn
[1Panel Log]: 项目文档: https://1panel.cn/docs
[1Panel Log]: 代码仓库: https://github.com/1Panel-dev/1Panel
[1Panel Log]:
[1Panel Log]: 如果使用的是云服务器，请至安全组开放 19870 端口
[1Panel Log]:
[1Panel Log]: 为了您的服务器安全，在您离开此界面后您将无法再看到您的密码，请务必牢记您的密码。
[1Panel Log]:
[1Panel Log]: ================================================================
```

## Debian/Ubuntu使用的是 UFW 防火墙。

1、更新软件包

```sudo apt update```

2、安装 UFW

```sudo apt install ufw```

3、如果你在远程位置连接你的服务器，在启用 UFW 防火墙之前，你必须显式允许进来的 SSH 连接。否则，你将永远都无法连接到机器上。

```sudo ufw allow 22/tcp```

如果 SSH 运行在非标准端口，你需要将上述命令中的 22 端口替换为对应的 SSH 端口。

4、放开 1Panel 系统端口。

```sudo ufw allow 19870/tcp```

上述命令中的 19870 端口需要替换为安装 1Panel 系统时自定义的端口。

5、启动 UFW

```sudo ufw enable```

### Debian 开启root ssh权限

```sudo vi /etc/ssh/sshd_config```

1.修改PermitRootLogin 没有找到可新建

``` PermitRootLogin yes ```



重启ssh 服务

``` sudo service ssh restart ```


## 终端命令添加 Docker 镜像加速

* 下是一整条命令，一起复制到终端运行

实时监测地址 https://status.1panel.top/status/docker
```
# 清空 /etc/docker/daemon.json 文件，准备写入新内容
echo >/etc/docker/daemon.json

# 使用 cat 命令将以下内容写入 /etc/docker/daemon.json 文件
# 配置 Docker 镜像加速器，使用多个镜像源来提高镜像下载速度
cat >/etc/docker/daemon.json <<EOF
{
  "registry-mirrors": [
    "https://proxy.1panel.live",
    "https://dockerproxy.cn",
    "https://hub1.nat.tf"
  ]
}
EOF

# 重启 Docker 服务以使配置生效
systemctl restart docker

```
1Panel 官方: https://proxy.1panel.live
			 
			 https://dockerproxy.1panel.live
			 
			 https://docker.1panel.live
			 
			 https://docker.1panel.top
			 
			 https://docker.1panel.dev


飞牛官网：https://docker.ketches.cn

棉花云官方：https://hub1.nat.tf / https://hub2.nat.tf

奶昔论坛官方: https://docker.naixi.net

DaoCloud 官方: https://docker.m.daocloud.io

木雷坞官方: https://docker.1ms.run

DockerProxy 官方: https://hub.rat.dev







https://docker.1panelproxy.com






xream/sub-store
xhofe/alist
youshandefeiyang/allinone
halohub/halo-pro
aircross/3x-ui
asdlokj1qpi23/proxypool
asdlokj1qpi23/subconverter





/opt/file/Proxypool



docker run -d --restart=always \
  --name=proxypool \
  -p 12580:12580 \
  -v /opt/file/Proxypool:/config \
  asdlokj1qpi23/proxypool \
  -c /config/config.yaml
  
  
  
docker run -d --restart=always -p 25500:25500 asdlokj1qpi23/subconverter:latest


http://39.188.154.94:25500/sub?target=v2ray&url=http://172.17.0.2:12580/clash/proxies


http://39.188.154.94:25500/sub?target=ss&url=http://172.17.0.2:12580/clash/proxies


http://39.188.154.94:25500/sub?target=clash&url=http://172.17.0.2:12580/clash/proxies

http://175.178.182.178:12580/clash/proxies
https://clashe.eu.org/clash/proxies
https://pp.dcd.one/clash/proxies
https://proxypool.neocities.org/clash/proxies
https://proxypool.link/clash/proxies

https://pandora-api.wanshanziwo.eu.org/api/tryourluck  随机节点

https://tgscan.onrender.com/sub9/base64
https://tgscan.onrender.com/sub10/base64
https://msnake.serv00.net/666.txt


##### 查看本机所有的容器

```docker ps -a```

##### 导出镜像

```docker export f299f501774c > hangger_server.tar```

##### 导入镜像

```docker import - new_hangger_server < hangger_server.tar```

##### 使用 save 和 load

##### 保存镜像
``` docker save 0fdf2b4c26d3 > hangge_server.tar ```

##### 载入镜像
``` docker load < hangge_server.tar ```




docker run -d --restart=always \
  --name=proxypool \
  -p 12580:12580 \
  -v /opt/file/Proxypool:/config \
  asdlokj1qpi23/proxypool \
  -c /config/config.yaml


docker run -d --restart=always \
  --name=SSRLive \
  -p 12580:12580 \
  -v /opt/file/Proxypool:/config \
  lukemin/ssrlive-proxypool \
  -c /config/config.yaml


./proxypool -d -c /config/config.yaml








https://im1907.top/?jx=', 'M1907解析接口'
https://svip.bljiex.cc/?v=', 'BL智能解析接口'
https://jx.m3u8.tv/jiexi/?url=', 'M3U8解析接口
https://www.8090g.cn/jiexi/?url=','8090解析接口
https://jx.xyflv.cc/?url=', '咸鱼解析接口
https://jx.yangtu.top/?url=','阳途解析接口
https://jx.2s0.cn/player/?url=', '极速解析接口
https://jx.qqwtt.com/?url=','剖云解析接口




https://yiqi-oss.oss-cn-hangzhou.aliyuncs.com/aliyun/technology/274915/249259.pdf


http://1worldenergy.com/wp-content/uploads/2020/05/GB-14866-2006-The-specifications-for-personal-eye-protectors.pdf



GB14866 site:yiqi-oss.oss-cn-hangzhou.aliyuncs.com



https://t.me/sharecentrepro
https://t.me/proxysharecn




## 一键安装Frp服务端

wget --no-check-certificate https://hao.iam7.cn/frps/install-frps.sh  -O ./install-frps.sh
chmod 700 ./install-frps.sh
./install-frps.sh install



wget --no-check-certificate https://hao.iam7.cn/frps/install-zh.sh -O ./install-zh.sh
chmod 700 ./install-zh.sh
./install-zh.sh install

./install-zh.sh uninstall

恭喜您, frps 安装成功!
================================================
You Server IP      : 139.28.232.96
Bind port          : 7000
KCP support        : true
vhost http port    : 8080
vhost https port   : 8443
Dashboard port     : 6443
token              : 02T5I07OD6jpNcoO
subdomain_host     : juzyz.cn
tcp_mux            : true
Max Pool count     : 50
Log level          : info
Log max days       : 3
Log file           : enable
================================================
frps Dashboard     : http://juzyz.cn:6443/
Dashboard user     : admin
Dashboard password : SflTJb3d
================================================

frps status manage : frps {start|stop|restart|status|config|version}


