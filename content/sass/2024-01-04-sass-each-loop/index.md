+++
title = "Sass 09: Each Loop"
draft = false
weight = 9
tags = ['css', 'sass']
+++

Perulangan sederhana menggunakan `@each`.

```scss
$list: (10px, 20px, 30px);

@each $item in $list {
  .pill-#{$item} {
    width: $item*2.5;
    height: $item;
  }
}
```
CSS:
```css
.pill-10px {
  width: 25px;
  height: 10px;
}

.pill-20px {
  width: 50px;
  height: 20px;
}

.pill-30px {
  width: 75px;
  height: 30px;
}
```