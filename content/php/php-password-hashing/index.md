---
title: PHP Password Hashing
weight: 14
tags:
  - PHP
---

Hasing password di PHP.

```php
<?php
$hash = password_hash($_SESSION["password"], PASSWORD_DEFAULT);
$passverify = password_verify($_SESSION["password"], $hash);

if ($passverify) {
	echo "Hash matched";
} else {
	echo "Incorrect password, try again!";
}
?>
```
