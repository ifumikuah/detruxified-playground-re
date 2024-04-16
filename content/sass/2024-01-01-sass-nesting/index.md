+++
title = "Sass 01: Intro dan Nesting"
draft = false
weight = 1
tags = ['css', 'sass']
+++

## CSS on Steroid

Sass adalah pre-processor untuk CSS, Sass berguna untuk mempermudah sintaks CSS kamu.

Sass bekerja dengan mengcompile sintaks `scss`/`sass` ke `css`.

Untuk dapat menggunakan Sass di projek, kamu butuh `sass` itu sendiri untuk mengcompile ke `css`, dan gunakan sebuah automation tools seperti [gulp](https://gulpjs.com/) atau [parcel](https://parceljs.org/languages/sass/) untuk mempermudah proses compile.

Perlu diingat bahwa Sass adalah sebuah pre-processing/ekstensi sama halnya seperti library javascript. Semua yang bisa dilakukan Sass pasti juga bisa dilakukan dengan vanilla CSS.

## Nesting

Nesting mengeliminasi penulisan sintaks yang berulang.

```scss
.parent {
  width: 30px;
  .child {
    padding: 10px;
    background-color: orange;
  }
}
```
Sama dengan:
```css
.parent {
  width: 30px;
}
.parent .child {
  padding: 10px;
  background-color: orange;
}
```

