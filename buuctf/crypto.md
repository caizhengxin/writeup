# Crypto

## MD5

> 题解

1. 使用在线cmd5工具，字符串查找

> flag{admin1}

## URL编码

> 题解

1. URL解码

> flag{and 1=1}

## 一眼就解密

> 题解

1. base64解码

> flag{THE_FLAG_OF_THIS_STRING}

## 摩丝

> 题解

1. 摩斯密码解码，转成大写

> flag{ILOVEYOU}

## 变异凯撒

> 题解

1. 密文前五位ascii与格式相差为5，6，7，8，9，写脚本

> flag{Caesar_variation}

## Quoted-printable

> 题解

1. 使用在线Quoted-printable解密

> flag{那你也很棒哦}

## password

> 题解

1. 姓名每个字的首字母，加上出生时间

> flag{zs19900315}

## 伪加密

> 题解

1. winhex打开，09->00

> flag{Adm1N-B2G-kU-SZIP}

## RSA

> 题解

1. 参考python-ctf rsa请d

> flag{125631357777427553}

## 丢失的MD5

> 题解

1. 运行题目脚本，拿到flag

> flag{e9032994dabac08080091151380478a2}

## 篱笆墙的影子

> 题解

1. 栅栏密码

> flag{wethinkwehavetheflag}

## Alice与Bob

> 题解

1. [分解素数](http://www.factordb.com/index.php)
2. [md5加密](https://www.cmd5.com/)

> flag{d450209323a847c8d01c6be47c81811a}

## Windows系统密码

> 题解

1. john --show --format=LM pass.hash

> flag{good-luck}

## rsarsa

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


def rsa_pqec(p: int, q: int, e: int, c: int) -> str:
    """解密
    """

    n = p * q
    d = int(gmpy2.invert(e, n - (p + q) + 1))

    return long_to_bytes(pow(c, d, n)), pow(c, d, n)
```

> flag{5577446633554466577768879988}

## 大帝的密码武器

1. 题解

```python
# 1. 凯撒密码爆破，得到有意思的单词
# 2. 拿到offset=13，加密明文
```

> flag{PbzrPuvan}

## 凯撒?替换?呵呵!

> 题解

1. https://quipqiup.com/

> flag{substitutioncipherdecryptionisalwayseasyjustlikeapieceofcake}

## RSA1

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


def rsa_pqdpdqc(p: int, q: int, dp: int, dq: int, c: int) -> tuple:
    """解密
    """

    n = p * q
    phin = (p - 1) * (q - 1)
    dd = gmpy2.gcd(p - 1, q - 1)
    d = (dp - dq) // dd * gmpy2.invert((q - 1) // dd, (p - 1) // dd) * (q - 1) + dq
    m = gmpy2.powmod(c, d, n)

    return long_to_bytes(m), m
```

> flag{W31c0m3_70_Ch1n470wn}

## 信息化时代的步伐

> 题解

1. [电报码，选择中文，数字代码](https://www.qqxiuzi.cn/bianma/dianbao.php)

> flag{计算机要从娃娃抓起}

## RSA3

> 题解

1. 共模攻击

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


def common_mode_attack(e1: int, e2: int, n: int, c1: int, c2: int) -> int:
    """Common mode attack
    """

    offset = 0

    gcd, s, t = gmpy2.gcdext(e1, e2)

    if s < 0:
        s = -s
        c1 = gmpy2.invert(c1, n)

    if t < 0:
        t = -t
        c2 = gmpy2.invert(c2, n)

    return (gmpy2.powmod(c1, s, n) * gmpy2.powmod(c2, t, n)) % n

m = common_mode_attack(e1, e2, n, c1, c2)
print(bytes.fromhex(hex(m)[2:]))
```

> flag{49d91077a1abcb14f1a9d546c80be9ef}

## old-fashion

> 题解

1. https://quipqiup.com/

> flag{n1_2hen-d3_hu1-mi-ma_a}

## 萌萌哒的八戒

> 题解

1. 猪圈密码

> flag{whenthepigwanttoeat}

## [AFCTF2018]Morse

> 题解

1. 摩斯密码解密，Hex字符串转ASCII字符串

> flag{1s't_s0_345y}

## 权限获得第一步

> 题解

1. 用在线cmd5解密F4AD50F57683D4260DFD48AA351A17A8

> flag{3617656}

## RSA2

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


def rsa_nedp(n: int, dp: int, e: int, c: int) -> tuple:
    """解密

    dp = d % (p - 1)

    c = m ^ e mode n
    m = c ^ d mode n

    """

    d = 0

    for i in range(1, e):
        if (dp * e - 1) % i == 0:
            if n % (((dp * e - 1) // i) + 1) == 0:
                p = ((dp * e - 1) // i) + 1
                q = n // (((dp * e - 1) // i) + 1)
                phi = (p - 1) * (q - 1)
                d = gmpy2.invert(e, phi) % phi

    m = gmpy2.powmod(c, d, n)
    return long_to_bytes(m), m
```

> flag{wow_leaking_dp_breaks_rsa?_98924743502}

## robomunication

> 题解

1. b替换成“.”,p替换成“-”
2. 摩斯解密

> flag{BOOPBEEP}

## RSA

> 题解

1. [提取公钥(e,n)](http://tool.chacuo.net/cryptrsakeyparse)

```python
e = 65537
n = 86934482296048119190666062003494800588905656017203025617216654058378322103517
```
2. [传入n获取p和q](http://www.factordb.com/index.php)

```python
p = 285960468890451637935629440372639283459
q = 304008741604601924494328155975272418463
```

3. 解密脚本

```python
import gmpy2
from Crypto.Util.number import long_to_bytes

e = 65537
n = 86934482296048119190666062003494800588905656017203025617216654058378322103517
p = 285960468890451637935629440372639283459
q = 304008741604601924494328155975272418463


def rsa_pqec(p: int, q: int, e: int, c: int) -> tuple:
    """解密
    """

    n = p * q
    d = int(gmpy2.invert(e, n - (p + q) + 1))
    m = pow(c, d, n)

    return long_to_bytes(m), m

if __name__ == "__main__":
    with open("flag.enc", "rb") as f:
        c = int.from_bytes(f.read(), byteorder="big")
        print(rsa_pqec(p, q, e, c))
```

> flag{decrypt_256}

## 异性相吸

> 知识：XOR

> 题解

```python
s = ""

with open("key.txt", "rb") as f1:
    with open("密文.txt", "rb") as f2:
        str1 = f1.read()
        str2 = f2.read()

        for i in range(len(str1)):
            s += chr(str1[i] ^ str2[i])

print(s)
```

> flag{ea1bc0988992276b7f95b54a7435e89e}

## 世上无难事

> 知识点：词频分析

> 题解

1. [quipquip](https://quipqiup.com/)在线解析

> flag{640e11012805f211b0ab24ff02a1ed09}

## 传感器

> 知识点: 曼切斯特编码

> 题解

```python
import textwrap

# 1. 曼切斯特编码，高->低(1), 低->高(0)
# 2. 差分曼切斯特编码，无跳变(1), 有跳变(0)


s = "5555555595555A65556AA696AA6666666955"
ss = ""

# 从右往左看
# 5 --> 0101 --> 11
# 6 --> 0110 --> 10
# 9 --> 1001 --> 01
# A --> 1010 --> 00

for v in s:
    ss += bin(int(v, 16))[2:].zfill(4)

ss = "".join(["1" if v == "01" else "0" for v in textwrap.wrap(ss, 2)])
ss = "".join([hex(int(v[::-1], 2))[2:] for v in textwrap.wrap(ss, 8)])

print("flag{" + ss.upper() + "}")
```

> flag{FFFFFED31F645055F9}

## 还原大师

> 知识点：MD5加密暴力破解

> 题解

```python
# -*- coding: utf-8 -*-
# @Author: JanKinCai
# @Date:   2020-03-18 22:44:25
# @Last Modified by:   JanKinCai
# @Last Modified time: 2020-03-28 16:29:39
import string
import hashlib

# ?表示大写字母
s = "TASC{}O3RJMV{}WDJKX{}ZM"
# E903???4DAB????08?????51?80??8A?
# 知识点：MD5加密暴力破解


def md5_crack(s: str, vaild: str) -> str:
    """爆破MD5
    """

    for v1 in string.ascii_uppercase:
        for v2 in string.ascii_uppercase:
            for v3 in string.ascii_uppercase:
                ss = s.format(v1, v2, v3)
                ss = hashlib.md5(ss.encode("utf-8")).hexdigest().upper()
                
                if ss.startswith(vaild):
                    return ss


print(md5_crack(s, "E903"))
```

> flag{E9032994DABAC08080091151380478A2}