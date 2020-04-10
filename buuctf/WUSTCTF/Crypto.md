# Crypto

## [WUSTCTF2020]babyrsa

> 知识点：RSA解密

> 题解

1. 分解n，http://www.factordb.com/index.php?query=86934482296048119190666062003494800588905656017203025617216654058378322103517
2. RSA解密

> flag{just_@_piece_0f_cak3}

## [WUSTCTF2020]dp_leaking_1s_very_d@angerou

```python
import gmpy2
from Crypto.Util.number import long_to_bytes, bytes_to_long


def rsa_n_e_c_dp(n: int, dp: int, e: int, c: int) -> bytes:
    """Known n dp e c, decrypto

    dp = d % (p - 1)

    c = m ^ e mode n
    m = c ^ d mode n

    """

    d = 0

    for i in range(1, e):
        v = dp * e - 1

        if v % i != 0:
            continue
        
        p = v // i + 1

        if n % p == 0:
            q = n // p
            d = gmpy2.invert(e, (p - 1) * (q - 1))

    return long_to_bytes(gmpy2.powmod(c, d, n))

print(rsa_n_e_c_dp(e=e, n=n, c=c, dp=dp))
```

> flag{dp_leaking_1s_very_d@angerous}

## [WUSTCTF2020]大数计算

> 知识点：数学知识

> 题解

```python
from functools import reduce
from sympy import *


x = Symbol("x")


def factorial(x):
    return reduce(int.__mul__, map(int, range(1, x + 1)))


part4 = hex((integrate(2*x, (x, 0, 22)) + 36) * 1314)[2:10]
part1 = hex(int(str(factorial(2020))[:8]))[2:10]
part2 = hex(int(str(520**1314 + 2333**666)[:8]))[2:10]
x = 80538738812075974
y = 80435758145817515
z = 12602123297335631
# https://posts.careerengine.us/p/5d732e4f6d74cb7af2d07915?nav=post_newest&p=5ae8c1d5138caf3e0e60207d
part3 = hex(int(str(x + y + z)[:8]))[2:10]

print("flag{" + "-".join([part1, part2, part3, part4]) + "}")
```

> flag{24d231f-403cfd3-108db5e-a6d10}

## [WUSTCTF2020]B@se

> 知识点：base64

> 题解

```python
import base64
import textwrap
from itertools import permutations

c = b"MyLkTaP3FaA7KOWjTmKkVjWjVzKjdeNvTnAjoH9iZOIvTeHbvD=="
table = "JASGBWcQPRXEFLbCDIlmnHUVKTYZdMovwipatNOefghq56rs{}kxyz012789+/"


def base64_decode(s: bytes, table: str) -> bytes:

    ss = "".join([bin(table.find(chr(v)))[2:].zfill(6) for v in s if 0x3d != v])
    ss = "".join([chr(int(v.zfill(8), 2)) for v in textwrap.wrap(ss, 8)])

    return ss


for v in permutations("34ju"):
    print(base64_decode(c, table.format("".join(list(v)))))
```

> flag{base64_1s_v3ry_e@sy_and_fuN}

## [WUSTCTF2020]情书

> 知识点：RSA

> 题解

```python
import string

import gmpy2
from Crypto.Util.number import long_to_bytes

lower_talbe = string.ascii_lowercase

n = 2537
d = 937
c = [156, 821, 1616, 41, 140, 2130, 1616, 793]

print("".join([lower_talbe[gmpy2.powmod(v, d, n)] for v in c]))
```

> flag{iloveyou}

## [WUSTCTF2020]佛说：只能四天

> 题解

```python
# 1. 新佛说解码，http://hi.pcmoe.net/buddha.html
# 2. 社会主义核心价值观解码，https://loli-rbq.top/socialist-core/test.html
#    RLJDQTOVPTQ6O6duws5CD6IB5B52CC57okCaUUC3SO4OSOWG3LynarAVGRZSJRAEYEZ_ooe_doyouknowfence
#    RLJDQTOVPTQ6O6duws5CD6IB5B52CC57okCaUUC3SO4OSOWG3LynarAVGRZSJRAEYEZ_ooe
# 3. 4位栅栏，https://www.qqxiuzi.cn/bianma/zhalanmima.php
#    R5UALCUVJDCGD63RQISZTBOSO54JVBORP5SAT2OEQCWY6CGEO53Z67L_doyouknowCaesar
#    R5UALCUVJDCGD63RQISZTBOSO54JVBORP5SAT2OEQCWY6CGEO53Z67L
# 4. 3位凯撒，http://ctf.ssleye.com/caesar.html
#    o5rxizrsgazda63onfpwqylpl54gsylom5pxq2lbnztv6zdbl53w67i 转换大写
# 5. base32解密
#    wctf2020{ni_hao_xiang_xiang_da_wo}
```

> flag{ni_hao_xiang_xiang_da_wo}