+++
title = "CSS Grid: Repeat function"
draft = false
weight = 7
tags = ['css']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "fig2.png"
title = ""

[[resources]]
name = "fig3"
src = "fig3.png"
title = ""
+++

Ini adalah fungsi untuk value property `grid-template-rows` dan `grid-template-columns`.

`repeat()` harus diisi dengan dua argument:

```css
.container {
    grid-template-rows: repeat(repetition, size);
    grid-template-columns: repeat(repetition, size);
}
```

- `repetition`, angka berapa banyak pengulangan dilakukan.
- `size`, ukuran di setiap pengulangan.

```css
.container {
    grid-template-rows: repeat(3, 5rem);
    grid-template-columns: repeat(3, 5rem);
}
```
Diatas akan membuat grid 3x3 dengan ukuran 5rem x 5rem disetiap itemnya.

## Repeated pattern

Jika kamu mengisi `size` dengan lebih dari satu value yang berbeda, maka akan membentuk pola yang sesuai dengan urutan secara berulang.

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 3rem 7rem);
    gap: 0.2rem;
}
```

{{< img name=fig1 size=small lazy=true >}}

Diatas akan membuat column 3rem dan 7rem secara berulang 3 kali, dan pada akhirnya membentuk total 6 column.