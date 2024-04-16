+++
title = "Sass 10: For Loop"
draft = false
weight = 10
tags = ['css', 'sass']
+++

For loop mirip dengan loop sebelumnya, namun disini for loop penggunaanya lebih praktis, perulangan dihitung berdasarkan nomor/index.

```scss
@for $i from 1 through 3 {
  // Code...
}
```
Diatas akan melakukan perulangan dari 1 sampai 3.

```scss
@for $item from 1 through 3 {
  $correct-value: $item*10;
  .pill-#{$correct-value}px {
    width: #{$correct-value*2.5}px;
    height: #{$correct-value}px;
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