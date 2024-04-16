+++
title = "Sass 04: Mixin II"
draft = false
weight = 4
tags = ['css', 'sass']
+++

Mixin dengan argument.

Ya, Mixin mengambil langkah yang lebih jauh untuk mengeliminasi repetisi dengan argument.

```scss
@mixin outer($bg-color, $radius) {
  background-color: $bg-color;
  padding: 8px;
  border: 2px solid white;
  border-radius: $radius;
}

section {
  @include outer(red, 25px);
}
```
Hasilnya:
```css
section {
  background-color: red;
  padding: 8px;
  border: 2px solid white;
  border-radius: 25px;
}
```

Argument bisa juga berupa variabel dengan tipe data yang sesuai.

```scss
$color-accent: red;

section {
  @include outer($color-accent, 25px);
}
```

## Default Value

*@mixin* bisa diberi default value sama halnya seperti fungsi pemrograman umunya.

```scss
@mixin outer($bg-color, $radius: 10px) {
  background-color: $bg-color;
  padding: 8px;
  border: 2px solid white;
  border-radius: $radius;
}
```

{{< hint type=note title="Urutan Parameter" >}}
**Prioritas Parameter**\
Parameter tanpa default value harus terletak diawal/sebelum parameter dengan default value.
{{< /hint >}}