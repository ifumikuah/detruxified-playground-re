---
title: PHP Loop
weight: 12
tags:
  - PHP
---

## For loop

```php
  <?php
    $ten = 10;
    
    for ($i = 1; $i <= $ten; $i++) {
      echo "Count is {$i} <br>";
    }
  ?>
```

## While loop

```php
<?php
	$i = 12;
	
	while ($i > 0) {
		echo "var i is: {$i} <br>";
		$i--;
	}
?>
```

Keyword `break` dan `continue`:

`break` akan membuat keluar dari blok while jika kriteria tertentu berlaku. Kode dibawah akan berhenti melanjutkan tepat disaat `$i` sama dengan `5`.

```php
<?php
	$i = 12;
	
	while ($i > 0) {
		if ($i == 5 ) { break };
		echo "var i is: {$i} <br>";
		$i--;
	}
?>
```

`continue` akan membuat sebuah perulangan dilompati jika kriteria tertentu berlaku di perulangan tersebut. Kode dibawah akan melompati angka genap.

```php
  <?php
  
    $i = 20;
    while ($i > 0) {
      if ($i % 2 == 0) {
        $i--;
        continue;
      }
      echo "var i is: {$i} <br>";
      $i--;
    }
  ?>
```
