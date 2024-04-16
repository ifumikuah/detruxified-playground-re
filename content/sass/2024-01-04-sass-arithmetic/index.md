+++
title = "Sass 08: Arithmetic"
draft = false
weight = 8
tags = ['css', 'sass']
+++

Sass menerima operasi aritmatika didalam variable maupun properti scss.

```scss
$def-margin: 8px;

.class {
  margin: $def-margin $def-margin*2
}
// Membuat margin 8px tinggi dan 16px kesamping kanan dan kiri
```

Operasi yang bisa diterima adalah `+`, `-`, `*`, `/` dan `%`.