# Misc

## 最简单的misc-y1ng

> 题解

1. 伪加密，winhex打开，搜索hex字符串504b0102, 后面09-->00
2. winhex打开解压之后的内容，发现是缺少png前四个字节，补完

```python
# with open("secret", "rb") as f:
# 	with open("secret.png", "wb") as f1:
# 		f1.write(b"\x89\x50\x4e\x47" + f.read())
```

3. 图片字符串转ASCII码

```python
import textwrap

print("".join([chr(int(v, 16)) for v in textwrap.wrap("424A447B79316E677A756973687561697D", 2)]))
```

> BJD{y1ngzuishuai}

## A_Beautiful_Picture

> 题解

1. winhex打开文件，修改图片高度

> BJD{PnG_He1ghT_1s_WR0ng}

## 小姐姐-y1ng

> 题解

1. winhex打开文件，搜索BJD

> BJD{haokanma_xjj}

## EasyBaBa

> 题解

1. foremost ezbb.jpg, 发现``有里面都是出题人.jpg``
2. winhex打开``有里面都是出题人.jpg``, 发现是avi格式，修改后缀
3. 观看视频，扫描4个二维码，拿到字符串转ASCII

> BJD{imagin_love_Y1ng}

## Real_EasyBaBa

> 题解

1. foremost ezbb_r.jpg
2. 打开分离出来的图片，发现二进制图案存在flag

> BJD{572154976}

## 圣火昭昭

> 题解

1. 右键图片详细信息，新佛曰解密http://hi.pcmoe.net/buddha.html
2. 根据提示gemlovecom去掉com
2. outguess -k 'gemlove' -r sheng_huo_zhao_zhao.jpg out.txt

> BJD{wdnmd_misc_1s_so_Fuck1ng_e@sy}

## TARGZ-y1ng

> 题解

```python
import os
import glob
import zipfile


filters = []


while 1:
    for file in glob.glob("*.tar.gz"):
        if file not in filters:
            filename = os.path.basename(file).split(".")[0]
            with zipfile.ZipFile(file) as zf:
                zf.extractall(pwd=filename.encode())
                zf.close()
                filters.append(os.path.basename(file))
                os.remove(file)

    with open("flag", "rb") as f:
        print(f.read())
        break
```

> BJD{wow_you_can_rea11y_dance}

## Imagin-开场曲

> 题解

1. 根据声音和每个字符串图形不同

> BJD{MIKUTAP3313313}