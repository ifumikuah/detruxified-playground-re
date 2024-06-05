---
title: PHP Cookie
weight: 8
tags:
  - PHP
---

Cookie adalah informasi non-sensitive yang tersimpan di browser, biasanya digunakan untuk mengambil informasi tentang preferensi kamu untuk kebutuhan periklanan, tautan yang sudah pernah dikunjungi, dan hal-hal tidak penting mengenai pengunjung dan situs tersebut.

## Membuat cookie

```plain
setcookie(name, value, expire, path, domain, secure, httponly)
```

Tiga value penting adalah: `name`, `value` dan `expire`.

```php
<?php
$cookie_name = "user";  
$cookie_value = "John Doe";

setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/");
?>
```

86400 adalah detik dalam satu hari, dikali 30 untuk total satu bulan masa berlaku cookie ini.

## Akses cookie

`$_COOKIE` adalah superglobal variable untuk mengakses cookie dalam bentuk associative array.

```php
<?php
foreach ($_COOKIE as $key => $val) {
	echo "{$key} => {$val}";
}
?>
```

## Hapus cookie

Untuk menghapus sebuah cookie, ubah valuenya menjadi kosong dan expirationnya menjadi masa lalu (value waktu minus).

```php
<?php
setcookie("user", "", time() - 3600);
?>
```

Gunakan `time()` untuk return waktu saat ini.
