+++
title = "jQuery: Selector"
draft = false
weight = 2
tags = ['javascript']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""
+++

Selector di jQuery sama seperti selector di CSS.

```js
$("h2") // Selects all h2 elements
$(".warning") // Selects all .warning class
$("#fish")  // Select id named #fish
```

Normalnya, selector di jQuery akan *return* list static dalam bentuk object, bukan array.

```js
$(document).ready(function(){
    console.log($(".select"));
})
```

{{< img name=fig1 size=medium lazy=true >}}

## Naming Convention

Kamu mungkin menyimpan sebuah selector jQuery dengan karakter `$` didepannya.

```js
$ThisJqueryRelatedThinggy = $(".selector")
$ThisJqueryRelatedThinggy.toggle()
```