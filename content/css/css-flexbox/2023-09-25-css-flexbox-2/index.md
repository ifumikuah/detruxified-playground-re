+++
title = "CSS Flexbox II"
draft = false
weight = 2
tags = ['css']

[[resources]]
name = "flexbox_1"
src = "flexbox-1.png"
title = ""

[[resources]]
name = "flexbox_2"
src = "flexbox-2.png"
title = ""

[[resources]]
name = "flexbox_3"
src = "flexbox-3.png"
title = ""

[[resources]]
name = "flexbox_4"
src = "flexbox-4.png"
title = ""

[[resources]]
name = "flexbox_5"
src = "flexbox-5.png"
title = ""
+++

Di flexbox, terdapat dua properti, satu untuk container itu sendiri dan untuk flex item didalamnya. Di catatan ini akan membahas Container properties.

## flex-direction

Flex-direction adalah arah sumbu untuk flexbox, value normalnya adalah `row`. Ada 4 value untuk `flex-direction`:

- `column`
- `column-reverse`
- `row`
- `row-reverse`

Flex-direction `column` akan membuat item flex mengikuti cross-axis, kebawah.

{{< img name=flexbox_1 size=medium >}}

`reverse` akan membuat urutan item menjadi terbalik, hal ini tidak disarankan karena akan membuat tampilan web dengan struktur HTML tidak sesuai.

## flex-wrap

Ketika lebar/tinggi container lebih kecil daripada jumlah item, maka item tersebut mengalami dua kondisi. 

`wrap` adalah ketika item tersebut melanjutkan barisnya di column/row baru, `nowrap` adalah ketika item tersebut terus melanjutkan sehingga keluar dari batasan container tersebut.

{{< img name=flexbox_2 size=medium >}}

Flexbox kiri memiliki `wrap` sedangkan yang kanan memiliki `nowrap`.

## justify-content

Justify content mengatur susunan item secara horizontal, main axis. Terdapat 5 nilai:

{{< img name=flexbox_4 size=small >}}

- `center`
- `flex-start`
- `flex-end`
- `space-around`
- `space-between`

## align-items

Mengatur item secara vertikal, cross axis.

{{< img name=flexbox_5 size=small >}}

- `center`
- `flex-start`
- `flex-end`
- `stretch`
- `baseline`

Flex start membuat item berawal dari atas container, sebaliknya end membuat item berawal dari bawah.

{{< img name=flexbox_3 size=small >}}

### Perfect Centering

Dengan menggabungkan `justify-content: center;` dan `align-items: center;`, kamu bisa membuat item didalam flexbox ditengah secara horizontal dan vertikal.