# 基于 IP 的规则

Surge 有 2 种基于 IP 的规则类型。如果请求的主机名是域名，则基于 IP 的规则将触发 DNS 查找。如果 DNS 查找失败，Surge 将中止规则测试并报告错误。

**IP-CIDR**

```text
IP-CIDR,192.168.0.0/16,DIRECT
IP-CIDR,10.0.0.0/8,DIRECT
IP-CIDR,172.16.0.0/12,DIRECT
IP-CIDR,127.0.0.1/8,DIRECT
```

如果请求的 IP 地址与指定的范围匹配，则执行规则策略。

**GEOIP**

```text
GEOIP,CN,DIRECT
```

如果 GeoIP 测试结果与指定的国家/地区代码匹配，则执行规则策略。

#### 基于 IP 的规则选项

```text
GEOIP,CN,DIRECT,no-resolve
IP-CIDR,172.16.0.0/12,DIRECT,no-resolve
```

遇到 GEOIP 或 IP-CIDR 规则时，Surge 会发送 DNS 问题以检查请求的主机名是否为域。您可以选择'no-resolve'选项来跳过此规则以处理具有域名的请求。

