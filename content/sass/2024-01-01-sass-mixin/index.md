+++
title = "Sass 03: Mixin"
draft = false
weight = 3
tags = ['css', 'sass']
+++

Mixin mengambil langkah yang lebih jauh untuk mengeliminasi repetisi.

Ada element kotak dengan posisi/class yang berbeda jauh satu sama lain, setiap kotak harus diberikan properti sebagai berikut:

```css
.outer {
  background-color: #5837a6;
  padding: 8px;
  border: 2px solid white;
  border-radius: 15px;
}
```

Satu satunya cara kita bisa membuat ini adalah dengan memberi class kalau di CSS, tapi *downside* cara ini pastinya akan "mengotori" namespace sehingga terlalu banyak class yang dipakai.

Sass menawarkan alternative, yaitu *@mixin*:

```scss
@mixin outer {
  background-color: #5837a6;
  padding: 8px;
  border: 2px solid white;
  border-radius: 15px;
}
```

lalu mixin diatas direferensikan dengan *@include*:

```scss
section {
  @include outer;
}

.about {
  font-family: Poppins, sans-serif;
  .infocard {
    color: #ded5f2;
    @include outer;
  }
}

.hotsale {
  margin: 2rem auto;
  @include outer;
}
```