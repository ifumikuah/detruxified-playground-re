+++
title = "Sass 13: Extends"
draft = false
weight = 13
tags = ['css', 'sass']
+++

Mirip seperti mixin, bedanya extend tidak menerima parameter dan sangat berguna jika ada dua komponen yang identik namun kamu hanya butuh sedikit perbedaan seperti warna atau shade.

```scss
.button-basic  {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}
```
Diatas adalah styling sebuah tombol basic.

Namun, kamu mungkin juga ingin memberi varian lain dari tombol lain ini, misalnya background merah untuk tombol darurat.

```scss
.button-warn {
  @extend .button-basic;
  background-color: red;
}
```
CSS:

```css
.button-basic, .button-report {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report  {
  background-color: red;
}
```

Dengan adanya ini, kamu tidak perlu membuat dua class di HTML kamu.

`<button class="button-basic button-report">Report this</button>`

Menjadi:

`<button class="button-report">Report this</button>`