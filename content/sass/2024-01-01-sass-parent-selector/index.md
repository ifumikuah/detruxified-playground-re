+++
title = "Sass 05: Parent Selector"
draft = false
weight = 5
tags = ['css', 'sass']
+++

Parent selector atau `&` merupakan keyword untuk mereferensi parent dari selector itu sendiri, ini berguna untuk pseudo-element dan pseudo-class.

CSS:
```css
.class {
  background-color: yellow;
}
.class:hover {
  transform: rotate(30deg);
}
```
Sass:
```scss
.class {
  background-color: yellow;
  &:hover {
    transform: rotate(30deg);
  }
}
```