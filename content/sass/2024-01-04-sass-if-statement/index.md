+++
title = "Sass 11: If Else"
draft = false
weight = 11
tags = ['css', 'sass']

[[resources]]
name = "sass-fig-1"
src = "sass-fig-1.png"
title = ""

[[resources]]
name = "sass-fig-2"
src = "sass-fig-2.png"
title = ""
+++

Menggunakan `if else` di Sass.

```scss
@mixin buttonify($outline: no-outline) {
  // Code...
  @if $outline == outline{
    outline: 3px solid $acc-color;
    border: 4px solid $bg-color;
  }
}
```
Diatas akan membuat dua variasi dari `buttonify` yaitu `buttonify(no-outline)` dan `buttonify(outline)`.

```scss
button {
  margin: 10px;
  &:nth-child(1) {
    @include buttonify(outline)
  }
  &:nth-child(2) {
    @include buttonify(no-outline)
  }
};
```

{{< img name=sass-fig-1 size=small lazy=true >}}

## Else

```scss
@mixin buttonify($outline: no-outline, $rounded: false) {
  // Code...
  @if $rounded {
    border-radius: 1rem;
  } @else {
    border-radius: 0;
  }
}

button {
  margin: 10px;
  &:nth-child(1) {
    @include buttonify(no-outline)
  }
  &:nth-child(2) {
    @include buttonify(no-outline, true)
  }
};
```

{{< img name=sass-fig-2 size=small lazy=true >}}