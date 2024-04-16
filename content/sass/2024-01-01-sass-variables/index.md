+++
title = "Sass 02: Variables"
draft = false
weight = 2
tags = ['css', 'sass']
+++

Sass menerima berbagai jenis tipe data untuk disimpan sebagai variable.

- **Numbers** seperti `1.5` atau `40px`.

- **String** seperti `"JetBrains Mono"` atau `sans-serif`.

- **Colors** kode warna hex(A), RGB(A), HSL(A) seperti `#3498db` atau `rgb(255, 0, 0)`.

- **Boolean** dalam bentuk `true` atau `false`.

- **List** merupakan comma atau space separated value yang mirip seperti sebuah array contohnya: `3px solid green` atau `10px, 30px, 60px`

- **Maps** fitur advanced yang menyimpan key-value data seperti object di JS, akan dibahas nanti.

## Demo

```scss
$small: 20px;
$color-accent: hsla(225, 54% ,43%, 0.8);
$border-default: 2px solid $color-accent;

.class {
  width: $small;
  .sub {
    background-color: $color-accent;
    border: $border-default;
  }
}

```
Sama dengan:
```css
--small: 20px;
--color-acent: hsla(225, 54% ,43%, 0.8);
/* CSS tidak bisa menyimpan list */

.class {
  width: var(--small)
}

.class .sub {
  background-color: var(--color-accent); 
  border: 2px solid var(--color-accent); 
```