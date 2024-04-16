+++
title = "CSS Grid II"
draft = false
weight = 2
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
+++

## Mengurus sebuah grid

Sesudah `.grid-container` diberi properti grid, tidak ada perubahan yang signifikan terhadap element-element di dalamnya.

Tetapi, CSS sudah menandai kalau `.grid-container` adalah sebuah container dan `.grid-item` sebagai items nya.

```html
<style>
    .grid-container {
        display: grid;
    }
    .grid-item {
        background-color: orangered;
    }
</style>
<div class="grid-container">
  <div class="grid-item"><p>1</p></div>
  <div class="grid-item"><p>2</p></div>
  <div class="grid-item"><p>3</p></div>
  <div class="grid-item"><p>4</p></div>
  <div class="grid-item"><p>5</p></div>
  <div class="grid-item"><p>6</p></div>
</div>
```

{{< img name=fig1 size=small lazy=true >}}

### Grid rows dan columns

Untuk membuat sebuah grid yang benar, kamu harus mendefinisikan jumlah dan ukuran dari row dan column grid.

`grid-template-rows`, mengatur rows (horizontal)
`grid-template-column`, mengatur columns (vertical)

jumlah rows dan columns adalah list ukuran yang dipisah oleh spasi.
jumlah spasi merepresentasikan jumlah/posisi dari column/row.

Contoh membuat sebuah grid 3 column dengan ukuran 80px column pertama dan 50px column 2 dan 3:

```css
.grid-container {
    display: grid;
    grid-template-columns: 80px 50px 50px;
}
.grid-item {
    background-color: orangered;
    border: solid black 0.1px; /* garis pembatas agar jelas */
}
```
{{< img name=fig2 size=small lazy=true >}}

Contoh lagi, membuat grid 2 column dengan ukuran 50px 50px, dengan row ukuran 60px 80px (dihitung dari atas).

```css
.grid-container {
    display: grid;
    grid-template-columns: 50px 50px;
    grid-template-rows: 60px 80px;
}
.grid-item {
    background-color: orangered;
    border: solid black 0.1px;
}
```

{{< img name=fig3 size=small lazy=true >}}

{{< expand "Apa yang terjadi dengan row ketiga ?" "🤔" >}}
Ketika kamu membuat sebuah grid dengan column yang lebih kecil daripada jumlah anak/item didalamnya, grid otomatis membuat row baru dibawahnya untuk mengisi sisa items yang ada.

Misal, jika kamu memiliki container dengan 16 item didalamnya: <br>
Ketika kamu membuat grid 4 columns, maka akan ada 4 rows dikarenakan 16 (items) / 4 (columns) = 4 (rows)
{{< /expand >}}

Masih di contoh yang sama, tapi kamu ingin membiarkan row pertama seperti biasa/default dan membuat row sesudahnya 80px 80px

```css
.grid-container {
    display: grid;
    grid-template-columns: 50px 50px;
    grid-template-rows: auto 80px 80px;
}
.grid-item {
    background-color: orangered;
    border: solid black 0.1px;
}
```

{{< img name=fig4 size=small lazy=true >}}