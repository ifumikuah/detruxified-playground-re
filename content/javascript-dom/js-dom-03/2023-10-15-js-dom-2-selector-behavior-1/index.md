+++
title = "Selector Behavior: querySelector"
draft = false
weight = 1
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

`.querySelector()` *return* satu selector CSS yang pertama muncul. Jika tidak tepat/salah nama akan *return* `null`.

Selector diisi dengan selector CSS dengan notasi *string*.

{{< hint type=note title="Info" >}}
Pseudo-elements dan pseudo-selector di CSS tidak bisa digunakan dalam DOM JavaScript
{{< /hint >}}

{{< img name=snippet1 lazy=true size=medium >}}
{{< img name=fig1 lazy=true size=medium >}}

Selama selector dapat dikenal/valid oleh CSS, selector tersebut tetap valid.

```js
const target = document.querySelector('.article > #special');
```
```js
const target = document.querySelector('.article.div #special');
```
