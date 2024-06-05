---
title: PHP Checkbox
weight: 6
tags:
  - PHP
---

Kode dibawah akan insert box terpilih kedalam array `animal`:

```php
  <form action="index.php" method="post">
    <div class="chekinput">
      <div class="checkbox">
        <input type="checkbox" name="animal[]" value="Horse" id="animal-horse">
        <label for="animal-horse">Horse</label>
      </div>
      <div class="checkbox">
        <input type="checkbox" name="animal[]" value="Kangaroo" id="animal-kangaroo">
        <label for="animal-kangaroo">Kangaroo</label>
      </div>
      <div class="checkbox">
        <input type="checkbox" name="animal[]" value="Duck" id="animal-duck">
        <label for="animal-duck">Duck</label>
      </div>
      <div class="checkbox">
        <input type="checkbox" name="animal[]" value="Lizard" id="animal-lizard">
        <label for="animal-lizard">Lizard</label>
      </div>
    </div>
    <button type="submit">Submit</button>
  </form>
  <?php
	  $input_array = $_POST["animal"];

	  foreach ($input_array as $key) {
	    echo "{$key} <br>";
	  }
  ?>
```

## List associate array $_POST

Superglobal variable `$_post` berisikan array associate dengan berisikan nilai attribute `name` dan `value`.

```php
<body>
  <form action="index.php" method="post">
    <div class="chekinput">
      <div class="checkbox">
        <input type="checkbox" name="Arabia" value="Horse" id="animal-horse">
        <label for="animal-horse">Horse</label>
      </div>
      <div class="checkbox">
        <input type="checkbox" name="Australia" value="Kangaroo" id="animal-kangaroo">
        <label for="animal-kangaroo">Kangaroo</label>
      </div>
      <div class="checkbox">
        <input type="checkbox" name="Norse" value="Duck" id="animal-duck">
        <label for="animal-duck">Duck</label>
      </div>
      <div class="checkbox">
        <input type="checkbox" name="Indonesian" value="Lizard" id="animal-lizard">
        <label for="animal-lizard">Lizard</label>
      </div>
    </div>
    <button type="submit">Submit</button>
  </form>
  <?php
  $input_array = $_POST;

  foreach ($input_array as $key => $val) {
    echo "{$key} => {$val} <br>";
  }
  ?>
</body>
```
