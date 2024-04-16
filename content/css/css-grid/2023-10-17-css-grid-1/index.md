+++
title = "CSS Grid I"
draft = false
weight = 1
tags = ['css']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "fig2.png"
title = ""
+++

Grid adalah sistem layout dua dimensi. sama seperti flexbox, namun grid menawarkan solusi yang lebih mudah skala yang lebih besar.

## Basic Terminology

{{< img name=fig1 size=medium lazy=true >}}

Ada dua dimensi dalam grid, yaitu row dan columns:
- Columns meliputi axis y / vertikal dari grid
- Rows meliputi axis x / horizontal dari grid

{{< img name=fig2 size=medium lazy=true >}}

## Define Grid

Untuk membuat sebuah grid, kamu membutuhkan:
- Sebuah container
- Element didalam container sebagai grid items

```html
<div class="grid-container">
  <div class="grid-item"><p>1</p></div>
  <div class="grid-item"><p>2</p></div>
  <div class="grid-item"><p>3</p></div>  
  <div class="grid-item"><p>4</p></div>
  <div class="grid-item"><p>5</p></div>
  <div class="grid-item"><p>6</p></div>
</div>
```
Struktur diatas adalah:
```plain
.grid-container
    |
    |- .grid-item
    |   |
    |   |- p
    |
    |- .grid-item
    |   |
    |   |- p
    |
    |- ...
```

Grid didefinisakan di selector container `.grid-container` dengan membuat properti `display: grid;`. Anak dari container, `.grid-item` otomatis menjadi grid items.

Hanya keturunan pertama (*direct descendants*) dari container yang akan menjadi grid items.