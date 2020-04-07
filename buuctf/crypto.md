# Crypto

## MD5

> 题解

1. 使用在线[cmd5](https://www.cmd5.com/)工具，字符串查找

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

1. 使用在线[Quoted-printable](http://www.mxcz.net/tools/QuotedPrintable.aspx)解密

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

```python
import gmpy2

p = 473398607161
q = 4511491
e = 17

d = int(gmpy2.invert(e, (p - 1) * (q - 1)))
print(d)
```

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

## RSAROLL

> 知识点：RSA加密/解密，分解p和q

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes

e = 19
n = 920139713
# 分解p和q：http://www.factordb.com/index.php?query=920139713
p = 18443
q = 49891

# (d * e) mod ((p - 1) * (q - 1)) = 1
# c = m ^ e mode n
# m = c ^ d mode n

d = int(gmpy2.invert(e, (p - 1) * (q - 1)))

m = ""

with open("data.txt", "rb") as f:
    f.readline()
    f.readline()

    while 1:
        ss = f.readline()

        if not ss:
            break
        c = int(ss.decode().replace("\n", ""))
        m += chr(gmpy2.powmod(c, d, n))

print(m)
```

> flag{13212je2ue28fy71w8u87y31r78eu1e2}

## RSA2

> 知识点：RSA wiener attack

> 题解

1. 通过这个脚本``https://github.com/pablocelayes/rsa-wiener-attack/blob/master/RSAwienerHacker.py``拿到d

> flag{47bf28da384590448e0b0d23909a25a4}

## Cipher

> 知识点：Playfair加密/解密

> 题解

1. Key为Playfair, 解密地址http://rumkin.com/tools/cipher/playfair.php

> flag{itisnotaproblemhavefun}

## Dangerous RSA

> 知识点：[低指数攻击](https://xz.aliyun.com/t/2731#toc-6)

> 题解

```python
import gmpy2

c = # ...
n = # ...
e = 3

k = 0

while 1:
    m, b = gmpy2.iroot(c + k * n, 3)
    if b == 1:
        print(bytes.fromhex(hex(m)[2:]))
        break
    k += 1
```

> flag{25df8caf006ee5db94d48144c33b2c3b}

## 达芬奇密码

> 知识点：移位

> 题解

```python
# S1和S2长度相同，对S1排序并排序S2
s1 = "1 233 3 2584 1346269 144 5 196418 21 1597 610 377 10946 89 514229 987 8 55 6765 2178309 121393 317811 46368 4181 1 832040 2 28657 75025 34 13 17711"
s1 = s1.split(" ")
s2 = "36968853882116725547342176952286"

print("flag{" + "".join([v for _, v in sorted(zip(s1, s2), key=lambda v: int(v[0]))]) + "}")
```

> flag{37995588256861228614165223347687}

## rot

> 知识点：移位(ROT13)

> 题解

1. [Rot13]解密

```
FLAG-I`-flagkp2k88kp2k84kp2k84kp2k84ykp2k80hikp2k86a{bak7syc|myikp2k80ykp2k83ek7skp2k86yg||dyYYYYkp2k8nk17MDOT@ReNc@O?R=Se>O=>RPS?=aac@Q>S=cbc
```

``表示看不懂``


[Rot13]: https://www.qqxiuzi.cn/bianma/ROT5-13-18-47.php

## RSA5

> 知识点：低指数广播攻击

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


nlist = []
clist = []
e = 0


def rsa_leb_attack(c: list, n: list, e: int) -> bytes:
    """低指数广播攻击

    知识点：公约数分解n
    """

    for i in range(len(n) - 1):
        for j in range(i + 1, len(n)):
            p = gmpy2.gcd(n[i], n[j])
            if p != 1:
                q = int(n[i] // p)
                d = gmpy2.invert(e, (p - 1) * (q - 1))
                return long_to_bytes(gmpy2.powmod(c[i], d, n[i]))


fmt = lambda v: int(v.split(b"=")[-1].replace(b" ", b"").rstrip(b"\n"))


with open("1.txt", "rb") as f:
    ss = f.readlines()
    for v in ss:
        if b"===" in v:
            continue

        if b"c" in v:
            clist.append(fmt(v))
        elif b"n" in v:
            nlist.append(fmt(v))
        elif b"e" in v:
            e = fmt(v)

print(rsa_leb_attack(clist, nlist, e))
```

> flag{abdcbe5fd94e23b3de429223ab9c2fdf}

## basic rsa

> 知识点：RSA解密

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes

p = 262248800182277040650192055439906580479
q = 262854994239322828547925595487519915551
e = 65533
n = p*q
c = 27565231154623519221597938803435789010285480123476977081867877272451638645710

# 先求d，再解密
d = gmpy2.invert(e, (p - 1) * (q - 1))
m = gmpy2.powmod(c, d, n)
print(long_to_bytes(m))
```

> flag{B4by_Rs4}

## bbbbbbrsa

> 知识点：RSA解密，爆破e，base64解密

> 题解

```python
# -*- coding: utf-8 -*-
# @Author: JanKinCai
# @Date:   2020-03-15 02:13:05
# @Last Modified by:   JanKinCai
# @Last Modified time: 2020-03-29 19:10:49
import base64
import random

import gmpy2
from Crypto.Util.number import long_to_bytes


p = 177077389675257695042507998165006460849
n = 37421829509887796274897162249367329400988647145613325367337968063341372726061
q = n // p
c = b"==gMzYDNzIjMxUTNyIzNzIjMyYTM4MDM0gTMwEjNzgTM2UTN4cjNwIjN2QzM5ADMwIDNyMTO4UzM2cTM5kDN2MTOyUTO5YDM0czM3MjM"
# 先反向，再base64解码
c = int(base64.b64decode(c[::-1]))

# e = random.randint(50000, 70000)
# 爆破e
for e in range(50000, 70000):
    if gmpy2.gcd(e, (p - 1) * (q - 1)) == 1:
        d = gmpy2.invert(e, (p - 1) * (q - 1))
        m = long_to_bytes(gmpy2.powmod(c, d, n))
        
        if b"flag{" in m:
            print(m)
```

> flag{rs4_1s_s1mpl3!#}

## [GUET-CTF2019]BabyRSA

> 知识点：简单数学，求 p * q

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes

# 由题已知
c = 0x50ae00623211ba6089ddfae21e204ab616f6c9d294e913550af3d66e85d0c0693ed53ed55c46d8cca1d7c2ad44839030df26b70f22a8567171a759b76fe5f07b3c5a6ec89117ed0a36c0950956b9cde880c575737f779143f921d745ac3bb0e379c05d9a3cc6bf0bea8aa91e4d5e752c7eb46b2e023edbc07d24a7c460a34a9a
e = 0xe6b1bee47bd63f615c7d0a43c529d219
d = 0x2dde7fbaed477f6d62838d55b0d0964868cf6efb2c282a5f13e6008ce7317a24cb57aec49ef0d738919f47cdcd9677cd52ac2293ec5938aa198f962678b5cd0da344453f521a69b2ac03647cdd8339f4e38cec452d54e60698833d67f9315c02ddaa4c79ebaa902c605d7bda32ce970541b2d9a17d62b52df813b2fb0c5ab1a5
# p + q
pq1 = 0x1232fecb92adead91613e7d9ae5e36fe6bb765317d6ed38ad890b4073539a6231a6620584cea5730b5af83a3e80cf30141282c97be4400e33307573af6b25e2ea
# (p + 1) * (q + 1) = pq + p + q + 1 
pq2 = 0x5248becef1d925d45705a7302700d6a0ffe5877fddf9451a9c1181c4d82365806085fd86fbaab08b6fc66a967b2566d743c626547203b34ea3fdb1bc06dd3bb765fd8b919e3bd2cb15bc175c9498f9d9a0e216c2dde64d81255fa4c05a1ee619fc1fc505285a239e7bc655ec6605d9693078b800ee80931a7a0c84f33c851740

# 求解p * q, n = pq2 - 1 - pq1
n = pq2 - 1 - (pq1)
m = gmpy2.powmod(c, d, n)
m = long_to_bytes(m)
print(m)
```

> flag{cc7490e-78ab-11e9-b422-8ba97e5da1fd}

## childRSA

> 知识点：Pollard's p-1

> 题解

方法一：

```python
import gmpy2
from Crypto.Util.number import long_to_bytes


# 由题已知
e = 0x10001
c = 26308018356739853895382240109968894175166731283702927002165268998773708335216338997058314157717147131083296551313334042509806229853341488461087009955203854253313827608275460592785607739091992591431080342664081962030557042784864074533380701014585315663218783130162376176094773010478159362434331787279303302718098735574605469803801873109982473258207444342330633191849040553550708886593340770753064322410889048135425025715982196600650740987076486540674090923181664281515197679745907830107684777248532278645343716263686014941081417914622724906314960249945105011301731247324601620886782967217339340393853616450077105125391982689986178342417223392217085276465471102737594719932347242482670320801063191869471318313514407997326350065187904154229557706351355052446027159972546737213451422978211055778164578782156428466626894026103053360431281644645515155471301826844754338802352846095293421718249819728205538534652212984831283642472071669494851823123552827380737798609829706225744376667082534026874483482483127491533474306552210039386256062116345785870668331513725792053302188276682550672663353937781055621860101624242216671635824311412793495965628876036344731733142759495348248970313655381407241457118743532311394697763283681852908564387282605279108
n = 32849718197337581823002243717057659218502519004386996660885100592872201948834155543125924395614928962750579667346279456710633774501407292473006312537723894221717638059058796679686953564471994009285384798450493756900459225040360430847240975678450171551048783818642467506711424027848778367427338647282428667393241157151675410661015044633282064056800913282016363415202171926089293431012379261585078566301060173689328363696699811123592090204578098276704877408688525618732848817623879899628629300385790344366046641825507767709276622692835393219811283244303899850483748651722336996164724553364097066493953127153066970594638491950199605713033004684970381605908909693802373826516622872100822213645899846325022476318425889580091613323747640467299866189070780620292627043349618839126919699862580579994887507733838561768581933029077488033326056066378869170169389819542928899483936705521710423905128732013121538495096959944889076705471928490092476616709838980562233255542325528398956185421193665359897664110835645928646616337700617883946369110702443135980068553511927115723157704586595844927607636003501038871748639417378062348085980873502535098755568810971926925447913858894180171498580131088992227637341857123607600275137768132347158657063692388249513


def Pollard_p_1(N):
    a = 2
    while True:
        f = a
        # precompute
        for n in range(1, 80000):
            f = gmpy2.powmod(f, n, N)
        for n in range(80000, 104729 + 1):
            f = gmpy2.powmod(f, n, N)
            if n % 15 == 0:
                d = gmpy2.gcd(f - 1, N)
                if 1 < d < N:
                    return d
        a += 1

# 求d

p = Pollard_p_1(n)
q = n // p
d = gmpy2.invert(e, (p - 1) * (q - 1))

# 解密
m = gmpy2.powmod(c, d, n)
print(long_to_bytes(m))
```

方法二：

```
1. yafu 分解n，拿到p和q
2. 再解密
```

> flag{Th3r3_ar3_1ns3cure_RSA_m0duli_7hat_at_f1rst_gl4nce_appe4r_t0_be_s3cur3}

## [GXYCTF2019]CheckIn

> 知识点：Base64、Rot47

> 题解

1. base64解码``v)*L*_F0<}@H0>F49023@FE0#@EN``
2. 发现``GXY{}``, offset=47, Rot47解密

```python
def rot47(s: bytes) -> bytes:
    """Rot47 Decode/Encode

    Args:
        param s (bytes): Value
    
    Returns:
        bytes
    """

    strs = [chr(v + 47 - 127 + 33 if v + 47 > 126 else v + 47) for v in s]

    return "".join(strs).encode()


print(rot47(b"v)*L*_F0<}@H0>F49023@FE0#@EN"))
# GXY{Y0u_kNow_much_about_Rot}
```

> flag{Y0u_kNow_much_about_Rot}

## 一张谍报

> 知识点：简单密码替换

> 题解

```python
# s3能对应到s2，所以s3对应s2的索引取出s1文字
s1 = "今天上午，朝歌区梆子公司决定，在每天三更天不亮免费在各大小区门口设卡为全城提供二次震耳欲聋的敲更提醒，呼吁大家早睡早起，不要因为贪睡断送大好人生，时代的符号是前进。为此，全区老人都蹲在该公司东边树丛合力抵制，不给公司人员放行，场面混乱。李罗鹰住进朝歌区五十年了，人称老鹰头，几年孙子李虎南刚从东北当猎户回来，每月还寄回来几块鼹鼠干。李罗鹰当年遇到的老婆是朝歌一枝花，所以李南虎是长得非常秀气的一个汉子。李罗鹰表示：无论梆子公司做的对错，反正不能打扰他孙子睡觉，子曰：‘睡觉乃人之常情’。梆子公司这是连菩萨睡觉都不放过啊。李南虎表示：梆子公司智商捉急，小心居民猴急跳墙！这三伏天都不给睡觉，这不扯淡么！到了中午人群仍未离散，更有人提议要烧掉这个公司，公司高层似乎恨不得找个洞钻进去。直到治安人员出现才疏散人群归家，但是李南虎仍旧表示爷爷年纪大了，睡不好对身体不好。"
s2 = "喵天上午，汪歌区哞叽公司决定，在每天八哇天不全免费在各大小区门脑设卡为全城提供双次震耳欲聋的敲哇提醒，呼吁大家早睡早起，不要因为贪睡断送大好人生，时代的编号是前进。为此，全区眠人都足在该公司流边草丛合力抵制，不给公司人员放行，场面混乱。李罗鸟住进汪歌区五十年了，人称眠鸟顶，几年孙叽李熬值刚从流北当屁户回来，每月还寄回来几块报信干。李罗鸟当年遇到的眠婆是汪歌一枝花，所以李值熬是长得非常秀气的一个汉叽。李罗鸟表示：无论哞叽公司做的对错，反正不能打扰他孙叽睡觉，叽叶：‘睡觉乃人之常情’。哞叽公司这是连衣服睡觉都不放过啊。李值熬表示：哞叽公司智商捉急，小心居民猴急跳墙！这八伏天都不给睡觉，这不扯淡么！到了中午人群仍未离散，哇有人提议要烧掉这个公司，公司高层似乎恨不得找个洞钻进去。直到治安人员出现才疏散人群归家，但是李值熬仍旧表示爷爷年纪大了，睡不好对身体不好。"
s3 = "喵汪哞叽双哇顶，眠鸟足屁流脑，八哇报信断流脑全叽，眠鸟进北脑上草，八枝遇孙叽，孙叽对熬编叶：值天衣服放鸟捉猴顶。鸟对：北汪罗汉伏熬乱天门。合编放行，卡编扯呼。人离烧草，报信归洞，孙叽找爷爷。"

res = ""

for i in range(len(s3)):
    for j in range(len(s2)):
        if s3[i] == strs2[j]:
            res += s1[j]
            break
print(res)
```

> flag{南天菩萨放鹰捉猴头}

## 这是什么

1. winhex打开文件，复制由``[]()``等字符组成的js代码
2. 打开浏览器F12, Console运行

> flag{a0448fd730b62c13ca80200c4529daa2}

## yxx

> 知识点：异或

> 题解

```python
s = ""

with open("密文.txt", "rb") as f:
    with open("明文.txt", "rb") as f1:
        s1 = f.read()
        s2 = f1.read()

        for i in range(len(s1)):
            s += chr(s1[i] ^ s2[i])

print(s)
# flag:nctf{xor_xor_xor_biubiubiu}
```

> flag{xor_xor_xor_biubiubiu}

## 鸡藕椒盐味

> 知识点：奇偶检验，纠错

```python
import hashlib
# 海明校验码纠错
print(hashlib.md5(b"110110100000").hexdigest())
```

> flag{d14084c7ceca6359eaac6df3c234dd3b}

## EasyProgram

> 知识点：代码阅读，编程

> 题解

```python
with open("file.txt", "rb") as f:
    ms = f.read()

key = "whoami"
s = list(range(256))
t = [key[i % len(key)] for i in range(256)]

j = 0

for i in range(256):
    j = (j + s[i] + ord(t[i])) % 256
    s[i], s[j] = s[j], s[i]

ss = ""
j = 0
i = 0

for m in range(38):
    i = (i + 1) % 256
    j = (j + s[i]) % 256
    s[i], s[j] = s[j], s[i]
    # 原题这行代码错误 set x:(s[i] + (s[j]mod(256))mod(256)) 应该改成 set x:(s[i] + (s[j]mod(256)))mod(256)
    x = (s[i] + (s[j] % 256)) % 256
    ss += chr(ms[m] ^ s[x])

print(ss)
```

> flag{f238yu28323uf28u2yef2ud8uf289euf}

## [AFCTF2018]你能看出这是什么加密么

> 知识点：RSA解密

> 题解

```python
import gmpy2
from Crypto.Util.number import long_to_bytes

p=0x928fb6aa9d813b6c3270131818a7c54edb18e3806942b88670106c1821e0326364194a8c49392849432b37632f0abe3f3c52e909b939c91c50e41a7b8cd00c67d6743b4f
q=0xec301417ccdffa679a8dcc4027dd0d75baf9d441625ed8930472165717f4732884c33f25d4ee6a6c9ae6c44aedad039b0b72cf42cab7f80d32b74061
e=0x10001
c=0x70c9133e1647e95c3cb99bd998a9028b5bf492929725a9e8e6d2e277fa0f37205580b196e5f121a2e83bc80a8204c99f5036a07c8cf6f96c420369b4161d2654a7eccbdaf583204b645e137b3bd15c5ce865298416fd5831cba0d947113ed5be5426b708b89451934d11f9aed9085b48b729449e461ff0863552149b965e22b6

d = gmpy2.invert(e, (p - 1) * (q - 1))
m = gmpy2.powmod(c, d, p * q)
m = long_to_bytes(m)
print(m)
```

> flag{R54_|5_$0_$imp13}

## [AFCTF2018]Vigenère

> 知识点：维吉密码爆破

密钥：csuwangjiang

> flag{Whooooooo_U_Gotcha!}

## [AFCTF2018]BASE

> 知识点：Base64/32/16

> 题解

```python
import base64


with open("flag_encode.txt",'rb') as f:
    ss = f.read()

while 1:
    try:
        ss = base64.b32decode(ss).decode()
    except Exception:
        try:
            ss = base64.b64decode(ss).decode()
        except Exception:
            try:
                ss = base64.b16decode(ss).decode()
            except Exception:
                print(ss)
                break

# afctf{U_5h0u1d_Us3_T00l5}
```

> flag{U_5h0u1d_Us3_T00l5}

## [AFCTF2018]Single

> 知识点：词频

> 题解

1. https://quipqiup.com/

> flag{Oh_U_found_it_nice_tRy}

## MagicNum

> 知识点：浮点数转ASCII码

```python
import struct


with open("where_is_flag.txt", "rb") as f:
    ss = f.read().decode().split("\r\n")


dd = b"".join([struct.pack("f", float(v)) for v in ss if v])
print(dd)
# afctf{sec_is_everywhere}
```

> flag{sec_is_everywhere}
