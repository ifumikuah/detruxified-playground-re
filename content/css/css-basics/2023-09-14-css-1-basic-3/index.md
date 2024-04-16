+++
title = "CSS Basic 03: Box Model I"
draft = false
weight = 3
tags = ['css']

[[resources]]
name = "box-model"
src = "box-model.png"
title = "Box Model"

[[resources]]
name = "border"
src = "border.png"
title = "Border"

[[resources]]
name = "padding"
src = "padding.png"
title = "Padding"

[[resources]]
name = "margin"
src = "margin.png"
title = "Margin"
+++

Sebelum memahami box model, ada baiknya mengetahui apa itu border, padding dan margin.

## Border

Merupakan garis batas yang mengelilingi konten.

```css
#content {
    font-family: sans-serif;
    color: blue;
    border:  5px solid green;
}
```

{{< img name=border size=medium >}}

## Padding

Spasi jarak antara konten dan border.

```css
#content {
   font-family: sans-serif;
   color: blue;
   border:  5px solid green;
   background-color: aquamarine;
   padding: 15px;
}
```
{{< img name=padding size=medium >}}

## Margin

Spasi jarak antara sebuah element dengan element lainnya, margin bersifat transparant dan memliki behavior yang cenderung sulit dipelajari.

```css
#content {
    font-family: sans-serif;
    color: blue;
    border:  5px solid green;
    background-color: aquamarine;
    padding: 15px;
    margin: 5px;
}
#content-2 {
    font-family: sans-serif;
    color: blue;
    border:  5px solid green;
    background-color: aquamarine;
    padding: 15px;
    margin: 5px;
}
```
{{< img name=margin size=medium >}}