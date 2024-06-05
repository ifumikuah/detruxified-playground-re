---
title: PHP String Function
weight: 17
tags:
  - PHP
---

Built-in function untuk string.

`strlen()`, return panjang string.

```php
$str = "Asmodeus";
$strlen = strlen($str);

echo "Theres {$strlen} characters in the word of {$str}";
```

`str_split()`, memecah string menjadi array.

```php
$str = "mississipi";
$arr = str_split($str);
    
foreach ($arr as $el) {
    echo $el . "<br>";
}
```

Jika ingin menggunakan delimiter, gunakan `explode()`.

```php
$str = "marco,pablo,juan";
$arr = explode(",", $str); // Memecah setiap koma (,)
    
foreach ($arr as $el) {
    echo $el . "<br>";
}
```

## Lainnya

- https://www.w3schools.com/php/php_ref_string.asp
- https://www.php.net/manual/en/ref.strings.php
