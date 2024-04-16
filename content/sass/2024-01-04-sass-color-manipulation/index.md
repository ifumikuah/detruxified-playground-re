+++
title = "Sass 07: Color Manipulation"
draft = false
weight = 7
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

## Alpha Color Manipulation

Manipulasi opasitas warna dengan `fade-in()` dan `fade-out()`.

```scss
$acc-color: #ed594e;

button {
  @include buttonify();
  &:nth-child(1) { // Button One
    background-color: $acc-color;
  };
  &:nth-child(2) { // Button Two
    background-color: fade-out($acc-color, 0.2);
  };
};
```

{{< img name=sass-fig-1 size=small lazy=true >}}

Hasil CSS nya:

```css
.section-1 button:first-child {
    background-color: rgb(237, 89, 78);
}
.section-1 button:nth-child(2) {
  background-color: rgba(237, 89, 78, 0.8);
}
```

## Sass:color

Gunakan modules `:color` untuk menggunakan ini dengan import:

```scss
@use 'sass:color';
```

### Mencampur dua warna dengan mix

```scss
button {
  @include buttonify(outline);
  $color-mix: color.mix(#ed594e, #525ceb, 50%);
  background-color: $color-mix;
  outline-color: $color-mix;
};
```

{{< img name=sass-fig-2 size=small lazy=true >}}

Diatas akan mencampur warna `#ed594e` dan `#525ceb` dengan proporsi 1:1 atau 50%, menghasilkan warna baru yaitu `#a05b9d`.

