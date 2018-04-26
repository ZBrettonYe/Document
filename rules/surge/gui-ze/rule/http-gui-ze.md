# HTTP 规则

Surge 有 2 种 HTTP 规则类型。HTTP 规则适用于 HTTP 请求或 HTTPS 请求，不会影响 TCP 连接。

**USER-AGENT**

```text
USER-AGENT,Instagram*,Proxy
```

如果请求与 User Agent 匹配，则执行规则策略。支持通配符 \* 和 ?。

### URL-REGEX

```text
URL-REGEX,^http://google\.com,Proxy
```

如果 URL 与正则表达式匹配，则执行规则策略。如果启用了 MitM，则可以将此规则用于 HTTPS 请求。

