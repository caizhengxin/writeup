# Misc

## 签到

> 题解

1. 描述给出了flag

> flag{buu_ctf}

## 金三胖

> 题解

convert aaa.gif q.png

> flag{he11ohongke}

## 二维码

> 题解

1. binwalk QR_code.png发现存在zip文件
2. foremost QR_code.png分离zip文件并提示密码4位数字
3. fcrackzip -b -c1 -l 4 -u xx.zip

> flag{vjpw_wnoei}

## N种方法解决

> 题解

1. file KEY.exe发现是txt文件
2. mv KEY.exe KEY.txt
3. 复制txt内容，通过浏览器打开二维码
4. 扫描二维码获取flag

> flag{dca57f966e4e4e31fd5b15417da63269}

## 大白

> 题解

1. 计算宽度，winhex修改
2. 打开图片获取flag

> flag{He1l0_d4_ba1}

## 基础破解

> 题解

1. rarcrack爆破

> flag{70354300a5100ba78068805661b93a5c}

## 你竟然赶我走

> 题解

1. winhex打开图片, 搜索flag

> flag{stego_is_s0_bor1ing}

## LSB

> 题解

1. zsteg发现存在png图片，另存为图片(二维码)，扫码拿到flag

> flag{1sb_i4_s0_Ea4y}

## 乌镇峰会种图

> 题解

1. winhex打开图片, 搜索flag

> flag{97314e7864a8f62627b26f3f998c37f1}

## rar

> 题解

1. 爆破

> flag{1773c5da790bd3caff38e3decd180eb7}

## ningen

> 题解

1. binwalk或者foremost分离内容，发现zip文件
2. 爆破fcrackzip -b -c1 -l 4 -u zip文件

> flag{b025fc9ca797a67d2103bfbc407a6d5f}

## qr

> 题解

1. 扫二维码：zbarimg xxx.png

> flag{878865ce73370a4ce607d21ca01b5e59}

## 文件中的秘密

> 题解

1. binwalk分析发现TIFF，邮件图片属性拿到flag

> flag{870c5a72806115cb5439345d8b014396}

## wireshark

> 题解

1. 用wireshark打开过滤80端口，右键追踪流

> flag{ffb7567a1d4f4abdffdb54e022f8facd}

## 镜子里的世界

> 题解

1. zsteg steg.png

> flag{st3g0_saurus_wr3cks}

## 小明的保险箱

> 题解

1. binwalk或者foremost分离rar文件
2. 爆破rar文件

> flag{75a3d68bf071ee188c418ea6cf0bb043}

## 爱因斯坦

> 题解

1. binwalk或者foremost分离zip文件
2. 查看图片属性，发现解压密码

> flag{dd22a92bf2cceb6c0cd0d6b83ff51606}

## 被嗅探的流量

> 题解

1. 使用wireshark打开文件，搜索flag

> flag{da73d88936010da1eeeb36e945ec4b97}

## 假如给我三天光明

> 题解

1. 参考盲文对照表，拿到解压密码
2. 解压文件，拿到音频文件，是摩斯密码
3. 使用Audacity分析，拿到flag

> flag{wpei08732?23dz}

## easycap

> 题解

1. wireshark提取TCP流

> flag{385b87afc8671dee07550290d16a8071}

## FLAG

> 题解

1. zsteg sss.png发现存在zip数据
2. 解压zip内容，拿到flag

> flag{dd0gf4c3tok3yb0ard4g41n~~~}

## 另一个世界

> 题解

1. winhex打开文件，发现最后存在二进制数据
2. 在线二进制转字符串

> flag{koekj3s}

## 荷兰带宽泄露

> 题解

1. 使用工具RouterPassView查找username

> flag{053700357621}

## 隐藏的钥匙

> 题解

1. 使用winhex打开搜索flag，base64解码

> flag{377cbadda1eca2f2f73d36277781f00a}

## 来首歌吧

> 题解

1. 使用Audacity打开文件，发现左声道是摩斯密码，解码拿到flag

> flag{5BC925649CB0188F52E617D70929191C}

## 后门查杀

> 题解

1. 使用查毒软件扫描，找到对应php文件，打开发现flag

> flag{6ac45fb83b3bc355c024f5034b947dd3}

## 神秘龙卷风

> 题解：

1. 爆破rar
2. https://www.splitbrain.org/services/ook提取flag

> flag{e4bbef8bdf9743f8bf5b727a9f6332a8}

## 梅花香之苦寒来

> 题解

1. winhex打开图片，发现一串字符串，转ascii字符串，坐标
2. 使用gnuplot画图

## snake

> 题解

1. binwalk分析图片，并分离出key和cipher
2. 打开key是base64解码，上网搜索，搜到关键anaconda(密钥)
3. 根据snake联想到serpent加密算法，在线解码拿到flag

> flag{who_knew_serpent_cipher_existed}

## 九连环

> 题解

1. binwalk -e xx.jpg 分离文件，zip
2. 伪加密修改解压得到jpg和zip
3. steghide extract -sf xxx.jpg, 得到zip解压密码
4. 解压zip拿到flag

> flag{1RTo8w@&4nK@z*XL}

## webshell后门

> 题解

1. 使用D盾扫描，打开文件拿到flag

> flag{ba8e6c6f35a53933b871480bb9a9545c}

## 数据包中的线索

> 题解

1. 分析TCP流，发现base64图片
2. 用chrome打开base64图片，格式data:image/jpg;base64,xxxxxxxx

> flag{209acebf6324a09671abc31c869de72c}

## 刷新过的图片

> 题解

1. java Extract ./Misc.jpg(git clone https://github.com/matthewgao/F5-steganography)
2. output.txt改成zip文件
3. 伪加密01 00  改成 00 00
4. 解压zip拿到flag

> flag{96efd0a2037d06f34199e921079778ee}

## 菜刀666

> 题解

1. wireshark打开分析流，发现有压缩包
2. foremost分离压缩包
3. 分析流7，发现base64编码的图片，存在解压密码

> flag{3OpWdJ-JP6FzK-koCMAK-VkfWBq-75Un2z}

## 蜘蛛侠呀

> 题解

1. 提取ICMPpayload，base64解密，发现是zip文件，解压
2. identify - format "%T" flag.gif(获取gif间隙数据)，拿到数据md5加密

> flag{f0f1003afe4ae8ce4aa8e8487a8ab3b6}

## [GXYCTF2019]佛系青年

> 题解

1. 伪加密，拿到txt佛语(图片是误导)
2. 在线解密佛语(与佛论禅)

> flag{w0_fo_ci_Be1}

## 小易的U盘

> 题解

1. 解压iso文件，发现很多autoflag.exe文件，并且有两个大小不一样，且有一个时间不一样
2. 用ida pro打开分析，找到_main_0, 拿到flag

> flag{29a0vkrlek3eu10ue89yug9y4r0wdu10}

## [RoarCTF2019]黄金6年

> 题解

1. winhex发现尾部存在base64编码字符串，并保存rar压缩包
2. 提取mp4里面的图片，拼接解压密码

> flag{CTF-from-RuMen-to-RuYuan}

## 黑客帝国

> 题解

1. 打开txt文件，发现是hex格式数据，分析发现是rar压缩包
2. 暴力破解rar压缩包，解压拿到png图片
3. winhex打开图片，发现头被修改，改回jpg头

> flag{57cd4cfd4e07505b98048ca106132125}

## [SWPU2019]伟大的侦探

> 题解

1. txt文件采用EBCDIC编码，解密wllm_is_the_best_team].
2. ]. 换成 !
3. 解密拿到很多图片，对应福尔摩斯  跳舞的小人

> flag{iloveholmesandwllm}

## USB

> 题解

1. 解压缩，拿到233.rar和key.ftm
2. 7a->74, 修复233.rar, 解压拿到233.png
3. 使用[StegOnline]获取蓝色0通道，存在二维码，拿到ci{v3erf_0tygidv2_fc0}
4. binwalk分离key.ftm, 拿到key.pcap
5. 提取key.pcap payload
6. 运行脚本，拿到KEY{XINAN}
7. 维吉尼亚密码解密fa{i3eei_0llgvgn2_sc0}
8. 栅栏解密

> flag{vig3ne2e_is_c00l}

## [V&N2020]拉胯的三条命令

> 题解

1. binwalk分析文件，并提取pcap文件
2. 根据提示，分析pcap文件端口扫描，找到存活端口，从小->大
3. 端口：21、22、631、801、3306

> flag{21226318013306}

## [V&N2020公开赛]ML 第一步

> 题解

> flag{8f6c4d5b-3ce7-4b66-a816-a25005246703}

## john-in-the-middle

> 题解

1. foremost xxx.pcap
2. 带旗子的图片LSB隐写

> flag{J0hn_th3_Sn1ff3r}

[StegOnline]: https://georgeom.net/StegOnline/image
