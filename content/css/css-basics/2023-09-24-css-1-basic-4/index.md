+++
title = "CSS Basic 04: Box Model II: Margin Collapse"
draft = false
weight = 4
tags = ['css']

[[resources]]
name = "margin_collapse_1"
src = "img-1.png"
title = "Margin collapse pada perbatasan box 1 dan box 2"

[[resources]]
name = "margin_collapse_2"
src = "img-2.png"
title = "Margin akan menjadi 50px, dikarenakan 50px > 30px"
+++

Seperti yang dijelaskan sebelumnya, margin memiliki sifat yang tidak dapat ditentukan jika tidak di handle dangan baik. Margin collapse adalah fenomena dimana dua element memiliki margin yang berbeda dan bertemu satu sama lain, tetapi hanya menghasilkan total margin yang terbesar.

{{< img name=margin_collapse_1 size=medium >}}

Box 1 dan 2 memiliki margin 30px semua sisi, ditengah-tengah margin box 1 dan 2, seharusnya memiliki total 60px dikarenakan 30px+30px, inilah yang dinamakan margin collapse.

Margin collapse hanya terjadi pada margin atas dan bawah.

## Apa yang terjadi jika ukuran margin berbeda?

{{< img name=margin_collapse_2 size=medium >}}

Jika ukuran yang berbeda, margin yang lebih besar akan selalu "melahap" nilai margin yang kecil. Seperti contoh diatas, margin-top box-2 diberi 50px dan margin-bottom box-1 diberi 30px.