+++
title = "CSS Grid Item: Area"
draft = false
weight = 6
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

`grid-area` adalah shorthand untuk `grid-column` dan `grid-row`.

```css
.grid-item-x {
    grid-area: row-start / column-start / row-end / column-end;
}
```

{{< img name=fig1 size=small lazy=true >}}

```css
.item-1 {
    grid-area: 2 / 2 / span 2 / span 2;
}
```

Detailed CSS rulesets:

```css
.grid-main {
    display: grid;
    grid-template-columns: repeat(4, 7rem);
    gap: 0.2rem;
}
.grid-m-item {
    min-height: 7rem;
    background-color: #192c4e;
    font-size: 1.5rem;
    padding: 0.5rem;
}
.item-1 {
  grid-area: 2 / 2 / span 2 / span 2;
}
```

## Grid area sebagai nama area

Kita dapat memberi nama pada item dengan property `grid-area`, lalu referensikan ke selector container dengan property `grid-template-areas`.

```css
.grid-main {
    display: grid;
    grid-template-columns: repeat(4, 7rem);
    gap: 0.2rem;
    grid-template-areas:
    "alpha alpha alpha alpha"
    ;
}
.item-1 {
    grid-area: alpha;
}
```

{{< img name=fig2 size=small lazy=true >}}

`alpha` mengambil 4 column di row pertama. Sangat tidak efisien jika kamu harus memberi nama per itemnya, Lebih baik menggunakan `grid-area` seperti biasanya.