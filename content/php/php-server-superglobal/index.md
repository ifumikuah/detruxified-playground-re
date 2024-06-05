---
title: PHP Server Superglobal
weight: 15
tags:
  - PHP
---

`$_SERVER` adalah superglobal yang menyimpan assosiative array, yang disimpan adalah semua informasi tentang halaman yang sedang dikunjungi. Ibaratnya environment variables pada page itu sendiri.

```php
echo $_SERVER['PHP_SELF'];
echo $_SERVER['SERVER_NAME'];
echo $_SERVER['HTTP_HOST'];
echo $_SERVER['HTTP_REFERER'];
echo $_SERVER['HTTP_USER_AGENT'];
echo $_SERVER['SCRIPT_NAME'];
```

```php
foreach ($_SERVER as $key => $value) {
	echo "{$key} : {$value} <br>";
}
```
