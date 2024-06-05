---
title: PHP $_GET dan $_POST
weight: 4
tags:
  - PHP
---

`$_GET` dan `$_POST` adalah superglobal variable php yang berguna untuk handling data formulir.

Keduanya menampung array yang didalamnya berisi key-value pair dari input yang dimasukkan.

## GET

GET mengirim form secara visible, artinya value yang dikirim terpampang jelas di URL. Ini sangat berguna jika ingin page dengan query tertentu di bookmark. Contoh kasusnya adalah pencarian / search query.

## POST

Mengirim form secara invisible, informasi yang dikirm tidak ada batasannya. Ini sangat berguna untuk data yang diperlukan sebelum backend processing atau kredensial. Contoh kasusnya adalah formulir register atau login.

## Example

1. POST:

```php
  <form action="index.php" method="post">
    <div>
      <label for="item_name">Name</label>
      <input type="text" name="item_name" id="item_name">
    </div>
    <div>
      <label for="item_qty">Quantity</label>
      <input type="number" name="item_qty" id="item_qty">
    </div>
    <button type="submit">Submit</button>
  </form>

  <?php
    $item_name = $_POST["item_name"];
    $item_qty = $_POST["item_qty"];
    $price = 20.00;
    $total = $item_qty * $price;
    
    echo "Total price of {$item_qty}x {$item_name} is \${$total}";;
  ?>
```

2. GET:

```php
  <form action="index.php" method="get">
    <label for="search">Search</label>
    <input type="text" name="search" id="search">
    <button type="submit">Submit</button>
  </form>
  
  <?php
    echo "Searching for {$_GET["search"]}";
  ?>
```
