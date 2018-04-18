# Surge 3

### 核心部分

- 性能优化：Surge 3 可从以下几个方面，优化全局的网络响应速度。

* DNS Round Robin 并发

当第一次访问拥有多条 A 和 AAAA 记录的域名时，Surge 将并发对所有 IP 地址发起 TCP 连接，提高 CDN 资源的访问速度。后续连接将优先使用第一次连接时速度最快的 IP 地址。

* DNS 并发查询

同时向所有可用的 DNS 服务器进行 DNS 查询。Surge 3 中对该功能的各项参数进行了进一步优化。

* TCP 优化

由 Surge 发出的 TCP 连接，全面使用 TCP\_NOTSENT\_LOWAT 和 TCP\_NODELAY 等现代网络优化参数，可使尚未对这方面进行优化的 App 得到响应速度的提升。

- 新的 Group 类型：fallback

基本与 url-test 一致，区别在于 fallback 只关心策略是否可用，并顺序选择最靠前的可用策略，并不关心测速结果的具体值。 

- FINAL 规则支持 dns-failed

FINAL 规则增加参数 dns-failed，当某请求在规则匹配阶段，如果需要本地 DNS 查询且查询失败，在 v2.x 中将产生 Rule Testing Failed 错误。配置该参数后，将在失败后直接使用 FINAL 规则而不产生错误。

_FINAL, proxy, dns-failed_

- 智能打断

在 v2.x 中，在切换 policy group 选择，会打断所有活动的连接。在 v3.0 后，会自动判断新的结果影响了哪些活动连接并进行打断，不再粗暴的打断所有连接。 

- HTTPS 代理支持客户端证书验证（client-side SSL/TLS certificate validation）

允许使用客户端证书进行 HTTPS 握手。暂不支持 UI 配置，配置样例：https://gist.github.com/Blankwonder/cd9fa1987e41cf1a1f1df50583ba1d9c 

- Header Rewrite

可配置规则对 HTTP/HTTPS 请求的 Header 进行修改，支持增加、删除以及替换字段，可按正则匹配特定 URL 进行修改。

- MitM on TCP

对于被 Surge TUN 接管的 raw TCP 请求，也可以强制开启 MitM 进行 HTTPS 解密了。该选项暂无 UI 配置。无特殊需求不建议启动。

_\[MITM\]_  
_tcp-connection=true_

- Pre-filter for capturing

可以在配置中设置抓取功能的 URL 关键词列表，配置后仅有命中关键词的请求会被记录。

- 极速切换

现在 Surge 在网络切换的时候可以直接过渡，不再需要等待 2 秒。

- 高并发优化

Surge 2.x 版本中，最高并发请求数只能达到 64 个（TCP 握手阶段），在 3.0 中得到了极大优化。

- HTTP pipelining

完整支持 HTTP 1.1 pipelining 特性。

- URL Rewrite 307

支持返回 HTTP 307，用于对 POST 请求进行重定向。 

- 猜测 HTTP 请求

对于被 Surge TUN 接管的 raw TCP 请求，Surge 会主动猜测是否为一个 HTTP 请求，并提取相应的 Request/Response Header。 

- TINYGIF 拒绝

新增规则类型 REJECT-TINYGIF，将会返回一个 1px 的透明 GIF 图片，用于特定情况的广告屏蔽。

- ICMP 转发

Surge 现在支持转发 ICMP 包了，开启 Surge 时 dig 等应用也可以正常工作了。

- UDP 转发

Surge 现在支持转发 UDP 包了，开启 Surge 时游戏也可以进行代理运行了。

### UI 部分

- Safari Extension

新增加 Safari 扩展，可以在 Safari 中为当前网页配置规则。

- iPad 支持优化

为 iPad 上各种使用方式（全屏，分屏，悬浮等）进行优化，不再简单的和 iPhone 版本使用一样的布局方式。

- JSON Viewer

抓取内容的 JSON 浏览器支持代码高亮了。

- Widget

Widget 中支持直接切换 Outbound Mode 和 Traffic Capture 开关，同时进行重构解决一些细节和稳定性问题。

- Touch ID / Face ID

可配置要求在开启 Surge 时或者编辑配置前验证 Touch ID / Face ID。 

- 相册模式

可使用相册模式快速预留抓取到的图片请求。

###  细节

- 请求列表界面显示目标 IP 的位置国旗  
- 在配置管理界面可以在配置上右滑进行强制 iCloud 同步  
- 保存图片时可以将 GIF 图片保存到系统相册了  
- 统计页面可以看到代理线路的 TCP RTT  
- 规则界面搜索可以搜到 FINAL 规则了  
- 删除代理服务器时能够选择如何处理相关规则了  
- 可选隐藏 Fabric/Crashlytics 的相关请求  
- 可选隐藏 Apple 的相关请求  
- 取消 bypass-system 选项  
- MitM 握手阶段效率大幅优化

以及众多细节调整与增强

