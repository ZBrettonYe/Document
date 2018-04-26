# Final 规则

FINAL 规则必须在其他规则之后写入。它决定了与任何规则不匹配的请求的默认策略。

```text
[Rule]
DOMAIN-SUFFIX,company.com,DIRECT
DOMAIN-KEYWORD,google,ProxyA
IP-CIDR,192.168.0.0/16,DIRECT
GEOIP,CN,DIRECT
FINAL,ProxyB
```

以上规则表示除了以下域名或 IP 都将由 FINAL 规则将流量引导至 ProxyB。

* `company.com`
* `google`
* `192.168.0.0/16`
* `GeoIP 测试结果为 CN（中国）`



{% hint style="info" %}
与 Workflow 生成的「☁️ Other」或「Other\_Proxy」分组同理
{% endhint %}

