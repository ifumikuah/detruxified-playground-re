---
title: PHP Include
weight: 10
tags:
  - PHP
---

`include` untuk include file halaman lain untuk modularitas.

Consider:
```plain
|- index.php
|
|- about.php
|
|- footer.html
|
|- header.html
```
Skenarionya ingin membuat header dan footer yang modular.

`index.php`:
```php
<?php
	include("header.html")
?>
<main>
	Content of the index page
</main>
<?php
	include("footer.html")
?>
```

`about.php`
```php
<?php
	include("header.html")
?>
<main>
	Content of the about page
</main>
<?php
	include("footer.html")
?>
```
