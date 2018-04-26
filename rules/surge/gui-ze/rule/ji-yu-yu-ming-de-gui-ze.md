# 基于域名的规则

**DOMAIN**

`DOMAIN,www.google.com,Proxy`

如果请求的域名完全匹配，则执行规则策略。

**DOMAIN-SUFFIX**

`DOMAIN-SUFFIX,google.com,Proxy`

如果请求的域名与后缀匹配，则执行规则策略。例如: 'google.com' 匹配 'www.google.com'、'mail.google.com'、'google.com'，但不匹配 'content-google.com'。

**DOMAIN-KEYWORD**

`DOMAIN-KEYWORD,google,Proxy`

如果请求的域名包含关键字，则执行规则策略。

### 基于域名的规则选项

**选项：force-remote-dns（仅限Surge iOS）**

```text
DOMAIN,www.apple.com,Proxy,force-remote-dns
DOMAIN-SUFFIX,apple.com,Proxy,force-remote-dns
DOMAIN-KEYWORD,google,Proxy,force-remote-dns
```

force-remote-dns 选项主要是为了解决有些域名在本地查询有障碍的问题（如公司内网域名）。

当域名带有 force-remote-dns 选项时，Surge 会直接返回一个 240.1.x.x 的 fake IP 并反向查出真正的域名是什么，避免本地的 DNS 查询动作。

这样虽然避免了本地 DNS 可能带来的干扰问题，但是因为返回了一个 fake IP，而 Surge 没有权限去强制清除系统或者应用的 DNS cache，所以在 Surge 关闭后可能导致一些问题，所以请谨慎的只给确实需要的域名开启这个选项。

