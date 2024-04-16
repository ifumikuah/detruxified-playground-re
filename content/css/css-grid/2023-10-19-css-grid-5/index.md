+++
title = "CSS Grid Item: Row/Columns"
draft = false
weight = 5
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

[[resources]]
name = "fig4"
src = "fig4.png"
title = ""

[[resources]]
name = "fig5"
src = "fig5.png"
title = ""

[[resources]]
name = "fig6"
src = "fig6.png"
title = ""
+++

Halaman ini menjelaskan singkat tentang properti `grid-row` dan `grid-column`. Sesuai judul halaman, properti ini di deklarasikan didalam selector item (direct children element).

## Sinopsis

Properti ini dapat mengkspansi sebuah item sesuai dengan posisi yang diinginkan.

{{< img name=fig1 size=medium lazy=true >}}

Container diatas memiliki 9 item didalamnya, namun beberapa item dapat diekspansi sehingga otomatis menggeser item terdekatnya. Berikut kodenya:

```css
.grid-container {
    background-color: #524948;
    display: grid;
    padding: 1rem;
    grid-template-columns: repeat(4, 10rem);
    grid-template-rows: repeat(4, 10rem);
    gap: 1rem;
}
.item-one {
    grid-row: 1 / 4;
}
.item-two {
    grid-row: 1 / 4;
}
.item-nine {
    grid-column: 3 / 5;
    grid-row: 3 / 5;
}
```

## Grid Row

Terdapat grid 3x3, kordinat dengan notasi `{row}, {column}`.

{{< img name=fig2 size=small lazy=true >}}

Pertama, kita harus memberi tanda di element item dengan memberi class.

```css
/* Ini ilustrasi html, bukan html asli punya diatas */
<div class="grid-container">
  <div class="grid-item item-one"><p>1</p></div>
  <div class="grid-item item-two"><p>2</p></div>
  <div class="grid-item item-three"><p>3</p></div>
  <div class="grid-item item-four"><p>4</p></div>
  <div class="grid-item item-five"><p>5</p></div>
  <div class="grid-item item-six"><p>6</p></div>
  <div class="grid-item item-seven"><p>7</p></div>
  <div class="grid-item item-eight"><p>8</p></div>
  <div class="grid-item item-nine"><p>9</p></div>
</div>
```

Setiap class memiliki satu identifikasi berbeda, disini kita akan menggunakan `item-five` di koordinat `2,2`.

### Row Start

`grid-row-start` untuk memulai `item-five` di row yang diinginkan.

{{< img name=fig3 size=medium lazy=true >}}

{{< hint type=important >}}
Jika kamu berusaha mengikuti kode yang sama persis seperti yang diatas, maka hasil yang kamu buat itu sudah benar. Kamu cukup pastikan item berada di row ke 3 dan column pertama.
{{< /hint >}}

Perhatikan jika kita memberi sebuah property `grid-row-start` membuat column juga pindah ke posisi pertama, ini dikarenakan kamu belum mendefinisikan dimana column `item-five` dimulai.

### Row End

`grid-row-end` untuk membuat posisi akhir dari `item-five`.

{{< img name=fig4 size=medium lazy=true >}}

### Shorthand

`grid-row: 2 / 4;` memiliki hasil sama dengan [yang diatas](#row-end).

{{< expand "Kenapa berakhir di row 4 ?" "🤔" >}}
Misal kamu ingin row 1 di ekspansi sampai row 2 (memakan 2 row), maka kamu harus membuat nilai ending 3 (row 2 + 1).

`grid-row: 1/3;` akan menggabungkan row pertama dan row kedua.
{{< /expand >}}

## Grid Column

Hukum `grid-row` juga belaku sama dengan column, hanya saja column mengatur posisi column.

- `grid-column-start`
- `grid-column-end`
- `grid-column`

Contoh membuat `grid-column: 1 / 3;`:

{{< img name=fig5 size=medium lazy=true >}}

Layout yang tidak diinginkan bisa saja terjadi jika kamu tidak mendefinisikan properti column dan row secara detail, pastikan selalu mendefinisikan `grid-column` dan `grid-row` di item yang di inginkan. Jangan lupa mengalokasikan jumlah item yang dibutuhkan.

Contoh, layout halaman artikel:

{{< img name=fig6 size=small lazy=true >}}

```css
.grid-main {
    display: grid;
    grid-template-columns: 5rem 10rem 10rem 5rem;
    grid-template-rows: 5rem 30rem 5rem;
    gap: 0.2rem;
}
.head {
    grid-row: 1;
    grid-column: span 4;
}
.mainpage {
    grid-column: 2 / span 2;
}
.foot {
    grid-column: span 4;
}
.ad-left {
    grid-row-start: 2;
}
```
```html
<div class="grid-main">
    <div class="grid-m-item head"><p>Header</p></div>
    <div class="grid-m-item mainpage"><p>Main</p></div>
    <div class="grid-m-item ad-left"><p>Ads</p></div>
    <div class="grid-m-item ad-right"><p>Ads</p></div>
    <div class="grid-m-item foot"><p>Footer</p></div>
</div>
```