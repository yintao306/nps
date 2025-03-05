
# nps
![](https://img.shields.io/github/stars/ehang-io/nps.svg)   ![](https://img.shields.io/github/forks/ehang-io/nps.svg)
[![Gitter](https://badges.gitter.im/cnlh-nps/community.svg)](https://gitter.im/cnlh-nps/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
![Release](https://github.com/ehang-io/nps/workflows/Release/badge.svg)
![GitHub All Releases](https://img.shields.io/github/downloads/ehang-io/nps/total)

[README](https://github.com/ehang-io/nps/blob/master/README.md)|[中文文档](https://github.com/ehang-io/nps/blob/master/README_zh.md)

nps是一款轻量级、高性能、功能强大的代理服务器。

## 特点
- 全平台兼容(linux、windows、macos、群辉等)，支持一键安装为系统服务
- 控制全面，同时支持服务端和客户端控制
- 操作简单，只需简单的配置即可在web ui上完成其余操作
- 展示信息全面，流量、系统信息、即时带宽、客户端版本等
- 扩展功能强大，该有的都有了（缓存、压缩、加密、流量限制、带宽限制、端口复用等等）

**没找到你想要的功能？不要紧，点击[进入文档](https://ehang-io.github.io/nps)查找吧**

## 快速开始

### 安装

#### 二进制安装
> [releases](https://github.com/ehang-io/nps/releases)

下载对应的系统版本即可，服务端和客户端是单独的

#### Docker部署

##### 服务端(nps)
```
# 方式一：从Docker Hub拉取镜像
docker pull YT8U8/NPS

# 运行容器
docker run -d --name nps \
    -p 8080:8080 \
    -p 8024:8024 \
    -v /path/to/conf:/conf \
    YT8U8/NPS

# 方式二：本地构建镜像
docker build -t nps -f Dockerfile.nps .

# 运行容器
docker run -d --name nps \
    -p 8080:8080 \
    -p 8024:8024 \
    -v /path/to/conf:/conf \
    nps
```

##### 客户端(npc)
```
# 方式一：从Docker Hub拉取镜像
docker pull YT8U8/NPS

# 运行容器
docker run -d --name npc \
    -v /path/to/conf:/conf \
    YT8U8/NPS -server=<server_ip>:<bridge_port> -vkey=<web界面中显示的密钥>

# 方式二：本地构建镜像
docker build -t npc -f Dockerfile.npc .

# 运行容器
docker run -d --name npc \
    -v /path/to/conf:/conf \
    npc -server=<server_ip>:<bridge_port> -vkey=<web界面中显示的密钥>
```

注意：
- 请将`/path/to/conf`替换为实际的配置文件目录
- 将`<server_ip>`替换为nps服务器的IP地址
- 将`<bridge_port>`替换为网桥端口（默认8024）
- 将`<web界面中显示的密钥>`替换为在Web管理界面中创建客户端时生成的密钥

### 服务端启动
下载完服务器压缩包后，解压，然后进入解压后的文件夹

- 执行安装命令

对于linux|darwin ```sudo ./nps install```

对于windows，管理员身份运行cmd，进入安装目录 ```nps.exe install```

- 默认端口

nps默认配置文件使用了8080，8024端口

8080为web管理访问端口

8024为网桥端口，用于客户端与服务器通信

- 启动

对于linux|darwin ```sudo nps start```

对于windows，管理员身份运行cmd，进入程序目录 ```nps.exe start```

```安装后windows配置文件位于 C:\Program Files\nps，linux和darwin位于/etc/nps```

**如果发现没有启动成功，可以查看日志(Windows日志文件位于当前运行目录下，linux和darwin位于/var/log/nps.log)**

- 访问服务端ip:web服务端口（默认为8080）
- 使用用户名和密码登陆（默认admin/123，正式使用一定要更改）
- 创建客户端

### 客户端连接
- 点击web管理中客户端前的+号，复制启动命令
- 执行启动命令，linux直接执行即可，windows将./npc换成npc.exe用cmd执行

如果需要注册到系统服务可查看[注册到系统服务](https://ehang-io.github.io/nps/#/use?id=注册到系统服务)

### 配置
- 客户端连接后，在web中配置对应服务即可
- 更多高级用法见[完整文档](https://ehang-io.github.io/nps/)

## 贡献
- 如果遇到bug可以直接提交至dev分支
- 使用遇到问题可以通过issues反馈
- 项目处于开发阶段，还有很多待完善的地方，如果可以贡献代码，请提交 PR 至 dev 分支
- 如果有新的功能特性反馈，可以通过issues或者qq群反馈
