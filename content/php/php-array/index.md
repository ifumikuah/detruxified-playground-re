---
title: PHP Array
weight: 5
tags:
  - PHP
---

Membuat array di PHP.

```php
$arrs = array("Apple", "Banana", "Chocholate", "Durian");
```

Mengakses isinya berdasarkan index (zero-indexed).

```php
$arrs = array("Apple", "Banana", "Chocholate", "Durian");

$arrval = $arrs[1];
echo $arrval;
```

Mengubah value `Chocholate`.

```php
$arrs = array("Apple", "Banana", "Chocholate", "Durian");

$arrs[2] = "Coconut"
echo $arrs[2];
```

## Array function

Fungsi built-in terkait array.

Array pop, membuang elemen terakhir dari array:
```php
$arrs = array("Apple", "Banana", "Chocholate", "Durian");
array_pop($arrs);

foreach($arrs as $e) {
	echo $e . "<br>";
};
```

Array push, memasukan item/s ke elemen terakhir array:
```php
$arrs = array("Apple", "Banana", "Chocholate", "Durian");
array_push($arrs, "Grape"); // Insert "Grape" to the array
array_push($arrs, "Pomegranate", "Lychee"); // You can also insert multiple values

foreach($arrs as $e) {
	echo $e . "<br>";
};
```

Lebih lanjut:
- https://www.w3schools.com/php/php_ref_array.asp
- https://www.php.net/manual/en/ref.array.php

## Associative array

Associative array adalah array yang memiliki value key-pair di setiap elemen nya.

```php
$animal = array(
	"fish" => "Marlin",
	"whale" => "Orca",
	"bear" => "Polar",
	"feline" => "Cheetah"
);

// Change value
$animal["bear"] = "Grizzly";

// Jika key belum ada, maka akan membuat key baru
$animal["dove"] = "Pigeon";

// Iterate array
foreach($animal as $key => $val) {
	echo "{$val} is {$key} <br>";
}
```
