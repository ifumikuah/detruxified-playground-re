+++
title = "jQuery: Event Handler"
draft = false
weight = 3
tags = ['javascript']
+++

`on()` adalah event handler di jQuery.

```js
// Syntax
$("#button").on('click', ()=>{
   // codes 
})
```

`'click'` bisa diganti dengan [event DOM HTML](https://www.w3schools.com/jsref/dom_obj_event.asp) lainnya.

## currentTarget

Menangkap properti event yang sedang di jalankan (*on fire*). Cara kerjanya persis seperti [callback](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) di `addEventListener()`.

```js
$(".demo-btn").click((event)=>{
    $(event.currentTarget.nextElementSibling).toggle()
})
```

Diatas akan `toggle` element saudara (element sesudahnya) dari `.demo-btn` tetapi spesifik hanya  untuk `.demo-btn` yang sedang di klik.

![jQuery Demo](/jquery/2023-10-23-jquery-3/gif1.gif)

## Chaining

Chaining memperpendek kode yang dibuat, alih alih mendeklarasikan ulang event baru dengan target yang sama, kita bisa *chaining* event di target yang sama.

```js
// Without chaining
$(".demo-btn").on("mousedown", (event)=>{
    $(event.currentTarget).html("Keep holding!!!")
})
$(".demo-btn").on("mouseup", (event)=>{
    $(event.currentTarget).html($initVal)
})

// With chaining
$(".demo-btn").on("mousedown", (event)=>{
    $(event.currentTarget).html("Keep holding!!!")
}).on("mouseup", (event)=>{
    $(event.currentTarget).html($initVal)
})
```
