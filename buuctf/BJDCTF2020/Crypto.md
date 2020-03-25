# Crypto

## 签到-y1ng

> 题解

1. base64

> BJD{W3lc0me_T0_BJDCTF}

## 老文盲了

> 题解

1. 拼音查询

> BJD{淛匶襫黼瀬鎶軄鶛驕鳓哵}

## cat_flag

> 题解

1. 每行8bit对应ASCII码

> BJD{M!a0~}

## 灵能精通-y1ng

> 题解

1. 变种猪圈密码

> flag{IMKNIGHTSTEMPLAR}

## 燕言燕语-y1ng

> 题解

1. 转成ASCII码
2. 维基亚密码解密，密钥yanzi

> BJD{yanzi_jiushige_shabi}

## Y1nglish-y1ng

> 题解

1. [在线解密](https://quipqiup.com/)
2. Cr4cy --> Cr4ck

> BJD{pyth0n_Brut3_f0rc3_oR_quipquip_AI_Cr4ck}

## rsa0

> 题解

```python
import gmpy2
from Crypto.Util.number import *

# a = p + q
# b = p - q
# c = c
# e = e

n = (a**2 - b**2) // 4
d = int(gmpy2.invert(e, n - a + 1))
print(long_to_bytes(pow(c, d, n)))
```

> flag{3b5f314b-7efc-4bd9-9f47-bf964ee7bd81}

## rsa1

> 题解

```python
import gmpy2
from Crypto.Util.number import *


# (p - q)^2 = p^2 + q^2 - 2pq ===> b^2 = a - 2n ===> n = (a - (b**2)) // 2
n = (a - (b**2)) // 2

a = # p^2 + q ^ 2
b = # p - q
c = # c
e = # e

# (p + q)^2 = p^2 + q^2 + 2pq
p_q = gmpy2.iroot(a + 2 * n, 2)[0]
# (p - 1) * (q - 1) = pq - (p + q) + 1
d = int(gmpy2.invert(e, n - p_q + 1))
p = pow(c, d, n)
print(long_to_bytes(p))
```

> flag{1b0ad21b-d258-480e-a816-938552486532}