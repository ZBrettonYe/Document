# Surge 2

**New Interface**

新版本自然在 UI 上会有很大修改，会很炫酷哦～

**Proxy Protocol**

* 新协议支持：SOCKS5 over TLS，配置方法

`Proxy = socks5, server.com, 1080, username, password, tls=true`

* SOCKS5 协议支持验证了
* 对于 SOCKS5 over TLS 和 HTTPS 协议，可以强制关闭证书名验证了

```
Proxy = https, server.com, 443, username, password, skip-common-name-verify=true
```

**Replica**

Replica 的功能已经被完全合并入 Surge 中，在设置中启动 Dump Traffic to Disk 后，所有 HTTP 协议的流量将会被抓取并存储。

同时，启动后，在请求列表界面中，可以直接看到图片缩略图了。

**IPv6**

该版本带来了 IPv6 的支持，目前已经可以支持以下常见的 IPv6 应用：

> IPv6 环境下

> ✅ 向 IPv6 的 DNS 服务器查询 AAAA 记录

> ✅ 向 IPv4 的 DNS 服务器查询 AAAA 记录

> ✅ 直接连接 IPv6 主机

> ✅ 通过 IPv6 的代理访问 IPv4 主机

> ✅ 通过 IPv6 的代理访问 IPv6 主机

> ❌ DNS Override

> ❌ 通过 TUN Interface 直接连接 IPv6 主机

> ❌ 通过 TUN Interface 向 IPv6 的 DNS 服务器查询

> IPv4 环境下

> ✅ 通过 IPv4 的代理访问 IPv6 主机 （服务端具备 IPv6 环境）

在双栈环境下，当某域名同时具有 A 和 AAAA 记录时，通过哪个协议访问的行为是随机的，之后会加上相关的策略选项。

目前需要使用参数启用 IPv6 支持

```text
[General]
ipv6 = true
```

**Surge CLI**

该部分功能详见之前的说明：https://medium.com/@Blankwonder/surge-cli-开始测试-70bef9fd7169

**SSID Settings**

支持在特定 SSID 下，执行某些特定的功能。目前仅支持临时暂停 Surge 工作，配置如下：

```text
[SSID Setting]
WiFi-SSID suspend=true
```

同时，Group 加入了一种新的类型：ssid （From TF 602）

可用于在某网络下使用特定线路

```text
[Proxy Group]
SSID-Group = ssid, default = Kdatacenter-KR, cellular = Linode-JP, UniFi-AC = DIRECT
```

其中 default 和 cellular 是保留字，用于指定数据网络下和没有特定规则时的线路，default 必填 cellular 可选。该 group 也可以和 select group 联合使用。_（什么，你 SSID 叫 default……？）_

**Today Widget**

* Widget Quick Start

启用该选项以后，从 Widget 开启 Surge 将不再需要开启 Surge 主界面了。开启该选项后会在系统 VPN 中建立一个 Widget 使用的 Profile。如果需要删除该 Profile，请先关闭该选项，然后唤起 Today Widget 一次。（由于系统问题，该 Profile 在 Surge 被卸载时，依然会遗留在系统里，请按照该操作方式删除）

* 线路切换选项折叠

默认情况下仅显示速度，点击展开按钮后可以切换线路。

**URL Rewrite**

* 支持以 302 方式进行 rewrite，可实现从 http 到 https 的跳转。

```text
[URL Rewrite]
^http://yachen.com https://yach.me 302
```

**Misc**

* 当配置被 iCloud 修改后，一旦 Surge 主界面被启动，将会自动重新加载新配置。
* 修正 Proxy 或者 Proxy Group 的名称中包含空格时引发的一些问题。
* 加入 Reset Warning Messages 选项
* 日志显示修改为等宽字体
* 在启动 Dump Traffic to Disk 后，对于 POST 请求也可以生成 curl 命令了
* 所有参数段都支持以引号进行分段，以包含特殊字符，如：

```text
[Proxy]
Proxy = https, server.com, 443, username, "pass,word"
[SSID Setting]
"WiFi SSID" suspend=false
```

