+++
title = "Sass 06: String Interpolation"
draft = false
weight = 6
tags = ['css', 'sass']
+++

String Interpolation adalah proses membuat sebuah "template" pada string, untuk memahami "String Interpolation" itu sendiri, mari lihat contohnya dalam javascript

```js
const strg = "Miles"
console.log(`Hello, my name is ${strg}`)
```

`${strg}` akan mencetak variable `strg` untuk ditampilkan

## String Interpolation di Sass

```scss
@mixin photo($file) {
  content: url('img/#{$file}.jpg');
}

.figure {
  @include photo('building');
  background-color: purple;
}
```
Akan menjadi CSS:

```css
.figure {
  content: url('img/building.jpg');
  background-color: purple;
}
```