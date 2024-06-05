---
title: PHP Isset
weight: 11
tags:
  - PHP
---

Fungsi `isset` mengecek apakah variable memiliki isi dan tidak null.

`isset` akan return `true` jika:
- variable diisi
- variable tidak diisi oleh `null`.

`isset` akan return `false` jika:
- variable tidak diisi
- variable diisi oleh `null`.

```php
$assigned = false;
$status = isset($assigned) ? "assigned" : "unassigned/null";

echo $status; // assigned
```

```php
$assigned = null;
$status = isset($assigned) ? "assigned" : "unassigned/null";

echo $status; // unassigned/null
```
