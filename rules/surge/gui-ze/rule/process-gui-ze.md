# Process 规则

您可以为指定的进程分配策略。Process 规则只适用于Surge for macOS，Surge iOS 将自动忽略这些规则。

**PROCESS-NAME**

```text
PROCESS-NAME,Telegram,Proxy
```

如果请求与进程匹配，则执行规则策略。支持通配符 \* 和 ?。

> 进程名称也是可执行文件的名称。macOS 的应用程序包位于路径 .app/Contents/MacOS。

