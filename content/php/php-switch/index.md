---
title: PHP Switch
weight: 18
tags:
  - PHP
---

```php
 <?php
   $ten_plus_nine = 21;

   switch ($ten_plus_nine) {
     case 19:
       echo "Correct !";
       break;
     case 21:
       echo "21?, You Stupid !";
       break;
     case 22:
       echo "22?, You Stupid !";
       break;
     default:
       echo "You Stupid !";
       break;
   }
 ?>
```

`break` akan membuat kode yang ada dalam blok `switch` tersebut berhenti ketika salah satu case ada yang benar.

Mekanisme dari `switch` adalah mengabaikan semua case **sampai** `case` yang bernilai benar ditemukan. Jadi `break` diperlukan agar `switch` langsung keluar dari blok eksekusi tepat disaat `case` yang benar ditemukan.
