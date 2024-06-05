---
title: PHP Quick Intro
weight: 1
tags:
  - PHP
---

## PHP Tags

Sebelum memulai, php harus dimulai dan diakhiri tags

```php
<?php
// Code belong here
?>
```

## Comment

```php
// Ini adalah one line comment
/*
	Ini adalah
	multiline comment
*/
```

## Echo

```php
echo "Hello World";
```

## Concatenate

Gunakan operator `.` untuk concat

```php
echo "Happy Cloud" . 9;
```

## Variabel

```php
$variable = "String";
$num = 20;
$NUM = 3.14;
$boolval = true;
$boolVal = false;

echo "Value of pi is {$NUM}";
```

PHP termasuk kedalam weakly typed language. Semua yang tertulis dalam kode PHP sifatnya case-insensitive **KECUALI** nama variable. dan jangan lupa akhiri baris dengan semicolon `;`.

## Null dan Boolean

`null` artinya belum diisi, atau akan diisi nanti.

Nilai boolean seperti `true` dan `false` di PHP akan direpresentasikan sebagai 1 dan *kosong* jika di `echo`.

## Arithmetic

```php
$x = 4;
$y = 16;
$z = 30;

$res = $z + ($y / $x) ** $x / $y; // 46
```

Urutan operasi sama seperti normalnya `() -> ** -> * -> / -> % -> + -> -`.
