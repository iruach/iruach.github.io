---
title: v2ray一键安装
catalog: v2ray
date: 2020-05-15 11:22:24
subtitle:
header-img:
tags: 
- v2ray
categories:
- v2ray
---

## 科学上网工具 V2Ray 简介及具体搭建流程

### 关于V2Ray


V2Ray是一个功能类似于Shadowsocks的代理工具，可以帮我们实现科学上网，支持 Socks、HTTP、Shadowsocks、VMess 等协议。


### V2Ray与Shadowsocks有什么区别

* 1.开发时间晚于Shadowsocks，功能更为强大，目前仍在维护更新。
* 2.使用自主VMess协议，不易被墙屏蔽。
* 3.网络传输效率更高，并且具有Mux多路复用功能，并发性能强
* 4.自带mKCP协议，可免去KCPTUN的安装。
* 5.可设置流量伪装，类似ShadowSocksR的混淆功能。
* 6.目前比较小众，被封锁的可能性较小。

### V2Ray的缺点：

1.目前SSR科学上网仍是主流，V2Ray的教程不多，上手稍慢。
2.因为功能强大，所有需要设置的参数稍多，不过已经有图形化界面了，设置并不复杂。

### 搭建V2Ray所需条件


其实搭建V2Ray的条件与SSR所需条件基本一致，并没有太特殊的。

V2Ray也是需要在国外VPS服务器上安装服务端，然后在本地设备上安装V2Ray客户端，设置好后客户端成功连接服务端就可以。

所以V2Ray的搭建流程：

* 购买一台国外VPS服务器。
* 一键安装V2Ray服务端。
* 在本地设备安装V2Ray客户端
* 连接成功。

下面我们分别介绍。

1.V2Ray服务器购买

之前在SSR的相关教程里，我们介绍过，国外VPS服务器并不贵，512M内存的VPS就够用了，平均每月大概十几块钱，相当于一碗面钱，可以用支付宝付美元，与日常网购区别不大。

用哪家的服务器，怎么购买

[搬瓦工](https://bandwagonhost.com/aff.php?aff=19935) 或 [Vultr](https://www.vultr.com/?ref=7887711-4F) 

2.在VPS服务器上安装V2Ray

2.1 Putty连接VPS服务器，复制以下命令输入开始安装：

```
wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/V2ray.Fun/master/install.sh && bash install.sh
```

如果运行以上命令时，出现找不到wget的英文提示，则表示系统没有安装wget，根据系统不同，选择以下命令安装：

`yum -y install wget`

2.2 V2Ray安装接近完成时，会提示输入用户名、密码、控制面板端口，可随意设置，如下图：

访问控制面板需要用这个端口，用户名和密码用于登录控制面板。

![](https://ssr.tools/wp-content/uploads/2018-07-26_183309.jpg)

2.3 正常来说，V2Ray已经安装成功了，可以尝试在浏览器打开控制面板地址。不过博主在这一步后无法打开V2Ray控制面板，可能是个例，保险起见，再复制以下命令运行：

`pip install Flask-BasicAuth`

2.4 以上命令运行完成后，我们再启动面板。Putty输入以下命令，然后选择1回车。如下图，提示V2ray.fun started，即表示启动成功。

![](https://ssr.tools/wp-content/uploads/2018-07-26_183519.jpg)

5.浏览器输入服务器IP+刚才设置的端口，访问V2Ray控制面板，输入用户名和密码登录，登录成功后的界面如下图所示：

![](https://ssr.tools/wp-content/uploads/2018-07-26_194039.jpg)

各项连接参数都显示在运行状态菜单。最下面的Vmess链接和二维码图片，都可以用于客户端连接。

### V2Ray控制面板设置
V2Ray.fun控制面板的修改连接菜单中，我们可以修改各项连接参数，如下图所示


* 运行控制：用于控制V2Ray的状态。
* UUID：用于客户端连接使用，默认是自动生成的，可以点击右侧按钮生成一个新的。
* 主端口：用于客户端连接的端口，可设置一个新的端口，然后点击右侧的修改端口进行修改。
* 加密方式：用于客户端连接的参数，不懂的话，默认即可。
* 传输方式：也是客户端连接参数之一，默认即可。
* TLS：不建议开启，默认是关闭的，右侧两个按钮是操作按钮，并非表示当前状态。
* Mux cool：多路复用功能，可提高并发连接性能，默认开启


以上各项参数设置完成后，就可以通过V2Ray客户端连接了。点击上图左侧的运行状态菜单，用V2Ray客户端扫描二维码即可连接，或者输入Vmess链接也可以

V2Ray各客户端下载、安装及使用教程可参考：

[V2Ray各平台客户端下载汇总 带图形化界面](https://ssr.tools/314)

参考链接：

[V2Ray一键安装脚本 自带图形化界面控制面板](https://ssr.tools/269)
