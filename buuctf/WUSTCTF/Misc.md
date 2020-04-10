# Misc

## [WUSTCTF2020]girlfriend

> 知识点：手机拨号，键盘密码

> 题解

1. 听声音，得到999 666 88 2 777 33 6 999 4 444 777 555 333 777 444 33 66 3 7777
2. 键盘密码解密，youaremygirlfriends

> flag{youaremygirlfriends}

## [WUSTCTF2020]spaceclub

> 题解

```python
import textwrap

with open("attachment.txt", "rb") as f:
    ss = f.read().decode("utf-8").split("\r\n")

# 短空格表示0, 长空格表示1
ss = "".join([str((0 if "      " == v else 1)) for v in ss if v])
ss = "".join([chr(int(v, 2)) for v in textwrap.wrap(ss, 8)])
print(ss)
# wctf2020{h3re_1s_y0ur_fl@g_s1x_s1x_s1x}
```

> flag{h3re_1s_y0ur_fl@g_s1x_s1x_s1x}

## [WUSTCTF2020]爬

> 题解

1. winhex打开，发现是pdf文件，修改后缀
2. 用pdf工具，移除图片
3. int转ASCII

```python
print(bytes.fromhex(hex(0x77637466323032307b746831735f31735f405f7064665f616e645f7930755f63616e5f7573655f70686f7430736830707d)[2:]))
```

> flag{th1s_1s_@_pdf_and_y0u_can_use_phot0sh0p}

## [WUSTCTF2020]find_me

> 题解

1. 右键属性盲文解密，https://www.qqxiuzi.cn/bianma/wenbenjiami.php?s=mangwen

> flag{y$0$u_f$1$n$d$_M$e$e$e$e$e}

## [WUSTCTF2020]alison_likes_jojo

> 题解

1. binwalk -e boki.jpg, 得到压缩包
2. AZPR 爆破zip，密码888866，解压之后WVRKc2MySkhWbmxqV0Zac1dsYzBQUT09
3. 多次base64解密

```python
import base64


def crack(s: bytes, *args, **kwargs) -> bytes:
    """Crack
    """

    count = 4 - len(s) % 4

    if count <= 2:
        s += b"=" * count

    while 1:
        try:
            s = base64.b32decode(s)
        except Exception:
            try:
                s = base64.b64decode(s).decode()
            except Exception as e:
                try:
                    s = base64.b16decode(s)
                except Exception:
                    return s

# killerqueen
```
5. outguess -k "killerqueen" -r jljy.jpg 1.txt

> flag{pretty_girl_alison_likes_jojo}