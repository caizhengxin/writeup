# Misc

## base64隐写

> 题解

```python
import textwrap
import string


base64_code = "".join([
    string.ascii_uppercase,
    string.ascii_lowercase,
    string.digits,
    "+/",
])


def base64_stego(path: str) -> str:
    """Base64 stego

    Args:
        param path (str): File path.

    Returns:
        str: flag
    """

    stegolist = []

    with open(path, mode="r", encoding="utf-8") as f:
        for i, bs in enumerate(f.read().split("\n"), 1):
            stegov = base64_stego_decode(bs)

            if stegov is not None:
                stegolist.append(stegov)

    flag = "".join([chr(int(bit, 2)) for bit in textwrap.wrap("".join(stegolist), 8) if int(bit) != 0 ])

    return flag


def base64_stego_decode(vstr: str) -> str:
    """Base64 stego decode
    
    Args:
        param vstr (str): base64 encode string.

    Returns:
        str: base64 decode stego bits
    """

    vstr += "=" * min((len(vstr) % 4), 2)
    count = vstr.count("=")

    if count < 1:
        return None

    bits = 0x0f if count == 2 else 0x03

    v = base64_code.find(vstr.replace("=", "")[-1]) & bits
    return bin(v)[2:].zfill(count * 2)


print(base64_stego("attachment/tmp/ComeOn!.txt"))
```

## swp

> 题解

1. binwalk -e xxx
2. rabin2 -zz flag | grep actf

> flag{c5558bcf-26da-4f8b-b181-b61f3850b9e5}

## outguess

> 题解

1. outguess -r mmm.jpg -k abc -t a.txt ; cat a.txt

> flag{gue33_Gu3Ss!2020}

## music

> 题解

1. 异或

```python
with open("vip.m4a", "rb") as f:
    with open("sss.m4a", "wb") as f:
        f.write(b"".join([(v ^ 0xa1).to_bytes(1, "big") for v in f.read()]))
```
2. 播放，拿到flag

> flag{abcdfghijk}

## 剑龙

> 题解

1. python stegosaurus.py -x O_O.pyc

> flag{3teg0Sauru3_!1}

## NTFS数据流

> 题解

1. 用7z打开压缩包，找到293.txt:flag.txt

> flag{AAAds_nntfs_ffunn?}

## 明文攻击

> 题解：

1. winhex打开woo.jpg图片，修改03 04前两个字节改成50 4B
2. foremost woo.jpg
3. 使用AZPR明文攻击

> flag{3te9_nbb_ahh8}

## frequency

> 题解

1. 右键easy.doc属性数据拿到base64后部分
2. 用office打开word，设置隐藏显示，拿到base64前部分
3. base64解码

> flag{plokmijnuhbygvrdxeszwq}