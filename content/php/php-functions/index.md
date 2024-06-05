---
title: PHP Functions
weight: 3
tags:
  - PHP
---

Membuat fungsi di PHP, sama seperti bahasa pemrograman pada umumnya.

```php
function sayhi () {
	echo "Hello World";
}

function addition($num1, $num2) {
	return $num1 + $num2;
}

$addition_res = addition(2, 2);

echo "Result is {$addition_res}";
echo addition(4, 4);
sayhi();
```

## Forced datatypes

Memaksa tipe data tertentu sebagai argument.

```php
function addition(int $num1, int $num2) {
	return $num1 + $num2;
}

$addition_res = addition("x", 2);
```

Nantinya akan muncul error jika yang di pass bukan integer, namun uniknya masih bisa menerima dan bahkan memproses angka integer yang dibungkus string.
