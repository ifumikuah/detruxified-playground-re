+++
title = "CSS Grid : Gap"
draft = false
weight = 3
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

Mengatur ukuran gaps dengan property `gap`.

```css
.grid-container {
    display: grid;
    grid-template-columns: 10rem 10rem 10rem;
    grid-template-rows: 10rem 10rem 10rem;
    gap: 1rem;
}
.grid-item {
    background-color: #CAFE48;
    border: solid #524948 2px;
}
```

{{< img name=fig1 size=small lazy=true >}}

## Row/Column Gap

`gap` bisa diganti dengan `row-gap` jika cuma ingin mengatur row gap.

{{< img name=fig2 size=medium lazy=true >}}

Hal ini berlaku juga untuk column dengan property `column-gap`.

## Shorthand

Shorthand dapat ditulis untuk property `gap` dengan format `gap: row column;`.

{{< img name=fig3 size=medium lazy=true >}}
