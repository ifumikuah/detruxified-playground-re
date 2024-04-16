+++
title = "Selector Behavior: getElementById"
draft = false
weight = 2
tags = ['javascript']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "snippet1"
src = "snippet1.png"
title = ""
+++

```js
const target = document.getElementById('para-2')
```

Sama seperti `querySelector()`, `getElementById()` *return* satu element yaitu sebuah id dalam dokumen HTML. notasi id(#) tidak perlu dibuat secara eksplisit, karena `getElementById()` hanya akan mencari id dalam dokumen.

Jika ingin target element dengan id, sebaiknya gunakan `getElementById()` dikarenakan lebih efisien.

{{< img name=snippet1 lazy=true size=medium >}}
{{< img name=fig1 lazy=true size=medium >}}

{{< hint type=note title="Info" >}}
Seperti `querySelector()`, jika id yang ditemukan lebih dari satu, maka akan *return* id yang pertama muncul. Id seharusnya unik dan nama yang diberikan tidak boleh dipakai lebih dari sekali.
{{< /hint >}}