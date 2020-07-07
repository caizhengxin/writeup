# Crypto

## Cube Crypto

- https://ctftime.org/writeup/18732

> flag{B D' R' D U F' R D L' D' R D B' L D' R' F U'}

## [UTCTF2020]basic-crypto

1. 二进制转ASCII

```python
import textwrap

with open("attachment.txt", "rb") as f:
    ss = f.read().decode("utf-8")


ss = "".join([chr(int(v, 2)) for v in textwrap.wrap(ss, 8)])
print(ss)
```
2. base64解码
3. 词频分析https://quipqiup.com/

> flag{n0w_th4ts_wh4t_i_c4ll_crypt0}