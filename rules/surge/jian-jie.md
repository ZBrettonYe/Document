# 简介

{% hint style="success" %}
官方手册：[https://manual.nssurge.com](https://manual.nssurge.com)

配置示例：

[中文版](http://nssurge.com/config-example/zhHans.conf)

[英文版](http://nssurge.com/config-example/en.conf)
{% endhint %}

{% hint style="info" %}
Surge 是基于 Network Extension 开发的一款网络调试工具，工作原理是使用 Packet Tunnel Provider 给系统套上一个代理。

Surge 会接管全局的（几乎）所有通信，所以所有网络通讯耗电（如 WiFi、4G）都会被算在 Surge 头上，实际上 Surge 的运行功耗很少，使用中也不会感到 Surge 对电量有明显影响。
{% endhint %}

{% hint style="danger" %}
Surge 不支持 ShadowsocksR
{% endhint %}

### Surge 的组件

#### Surge Proxy Server \(Surge Core\) {#surge-proxy-server-surge-core}

这是 Surge 的核心部分。它是一个全功能的 HTTP / SOCKS5 代理服务器，具有高性能和稳定性，以Objective-C 编写并针对 iOS 和 macOS 进行了优化。

#### Surge TUN \(仅 iOS 版本\) {#surge-tun-ios-version-only}

有些应用程序不遵守系统代理设置（如 Mail.app），因为它们需要使用原始的 TCP socket。这种流量则由 Surge TUN 处理。

这是 Surge for iOS 的架构： 

![](https://manual.nssurge.com/Surge-Architecture.png)

#### Surge Dashboard \(仅 macOS 版本\) {#surge-dashboard-mac-version-only}

Surge Dashboard 是一个图形用户界面，可以用于查看和检查请求，列出DNS缓存并修改配置。当设置外部控制器访问时，它可以连接到本地实例或远程实例。

#### Surge CLI \(仅 macOS 版本\) {#surge-cli-mac-version-only}

Surge CLI is a command line tool to control Surge. It's bundled in mac version. Just like Surge Dashboard, it can connect to a local Surge instance, or a remote instance when the external-controller-access is set.

