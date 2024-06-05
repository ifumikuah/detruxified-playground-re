---
title: PHP Connect to mysql server (mysqli)
weight: 7
tags:
  - PHP
---

Connect ke database mysql dengan mysqli.

## Membuat koneksi

Buat sebuah file `conn.php` untuk handling koneksi ke server mysql.

```php
<?php
	// Kredensial mysql
	$servername = "localhost";
	$username = "detrux";
	$password = "Root1234";
	$dbname = "office_b1";

	// Mencoba connect ke server
	try {
		$conn = mysqli_connect($servername, $username, $password, $dbname)
	} catch (mysqli_sql_exception) {
		echo "Fail to connect!";
	}
?>
```

`$conn` aka melemparkan exception `mysqli_sql_exception`, jika operasi gagal. Jika gagal, `echo` pesan yang tertera.
