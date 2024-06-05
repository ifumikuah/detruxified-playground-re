---
title: PHP Session
weight: 16
tags:
  - PHP
---

Session menyimpan sesi user yang login (di situs) saat ini.

## Memulai sebuah session

Dipaling atas halaman yang ingin diberi sesi, kamu harus menginisialisasi sesi dengan memanggil `session_start()`.

```php
<?php
session_start()
?>
// Html codes below
```

Membuat variable sesi dengan superglobal `$_SESSION`, biasanya yang disimpan adalah terkait keredensial sperti username, email atau password.

```php
<?php
$_SESSION["username"] = "epicgamer420";
$_SESSION["email"] = "ibeatmeat@mail.me";
?>
```

## Menjalankan sesi di halaman lain

Jika sesi sudah diatur sebelumnya seperti yang diatas, kamu tinggal memanggil `session_start()` untuk mengambil info sesi sebelumnya.

```php
<?php  
session_start();  
?>
// Html for about.php below
```

## Destroy sesi

Ibarat kata kamu ingin logout dari sebuah situs, pasti informasi login yang tersimpan disitus sebelumnya akan di hapus dan kamu di tendang ke halaman login.

Jika `logout_btn` bernilai `true`, maka infoermasi tentang sesi akan dihapus dan dihancurkan.

```php
<?php
// Initialization
session_start();
?>
// HTML Codes...
<?php
	if ($logout_btn) {
		session_unset();
		session_destroy();
	}
?>
```
