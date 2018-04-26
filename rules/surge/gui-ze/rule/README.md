# \[Rule\]

此文档的系统环境

{% hint style="info" %}
系统版本：iOS 11.4 \(15F5037c\)

软件版本：Surge 3.2.0 \(Build 1144 BTEA, v3-0e9697d\)
{% endhint %}

### 优先级

Surge 从上至下按照它们在配置文件中出现的顺序进行匹配。换句话说，列表顶部的规则比后面的规则具有更高的优先级。

### 结构

Surge 配置由以下部分组成。

> `[General]`
>
> `[Replica]`
>
> `[Proxy]`
>
> `[Proxy Group]`
>
> `[Rule]`
>
> `[Host]`
>
> `[URL Rewrite]`
>
> `[Header Rewrite]`
>
> `[SSID Setting]`
>
> `[MITM]`

Surge 支持 9 种不同类型的规则，代理策略必须使用其中一个策略名称命名，包括"代理"、"策略组"、"DIRECT" 和 "REJECT"，尾部必须以 FINAL 结束以定义默认行为。

> `[Rule]`
>
> `PROCESS-NAME,WeChat,DIRECT`
>
> `USER-AGENT,QQ*,DIRECT`
>
> `DOMAIN,ip.bjango.com,DIRECT`
>
> `DOMAIN-SUFFIX,company.com,DIRECT`
>
> `DOMAIN-KEYWORD,google,ProxyA`
>
> `URL-REGEX,*apple.com/cn,ProxyB`
>
> `IP-CIDR,192.168.0.0/16,DIRECT`
>
> `GEOIP,CN,DIRECT`
>
> `FINAL,ProxyB`

