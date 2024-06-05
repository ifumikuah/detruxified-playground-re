---
title: PHP If Else...
weight: 2
tags:
  - PHP
---

```php
<?php
$age = 16;

if ($age >= 18) {
	echo "You can drink";
} else {
	echo "Can't drink right now!";
}
?>
```

Menggunakan else if:

```php
<?php
$age = 20;

if ($age > 40) {
	echo "Just don't drink too much!"
} elseif ($age >= 18) {
	echo "You can drink";
} else {
	echo "Can't drink right now!";
}
?>
```

## Logical Operators

Logical operator yang tersedia adalah `&&`, `||` dan `!` (AND, OR, dan NOT).

```php
<?php
	// Nuremburg Youth Competition
    $age = 36;
    $isNuremburg = false;

    if ($age >= 18 && $age < 36) {
      echo "You're allowed to participate!<br>";
      if (!$isNuremburg) {
        echo "You're not based in Nuremburg, please register before 15th May!<br>";
      }
    } else {
      echo "You're not allowed to participate!<br>";
    }
?>
```

## Ternary Operators

```php
$age = 18;
$isYoung = $age > 16 && $age < 36 ? "true" : "false";
    
echo $isYoung; // true (string)
```

