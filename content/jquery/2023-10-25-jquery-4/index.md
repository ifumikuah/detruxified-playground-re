+++
title = "jQuery: CSS Styling"
draft = false
weight = 4
tags = ['javascript']
+++

Interactive CSS Styling dengan jQuery.

## Menggunakan css method

`.css()` Method berguna untuk mengganti styling CSS dari selected element.

```js
let $initVal = $(".demo-btn").html()
$(".demo-btn").on("mousedown", (event)=>{
    $(event.currentTarget).html("Keep holding!!!")
    .css({
        backgroundColor: 'red',
        outlineColor: 'red'
    })
}).on("mouseup", (event)=>{
    $(event.currentTarget).html($initVal)
    .css({
        backgroundColor: '',
        outlineColor: ''
    })
})
```

![jQuery Demo](/jquery/2023-10-25-jquery-4/gif1.gif)

Untuk property CSS sama seperti properti vanilla JS, tapi bedanya dibungkus dalam object.

Contoh:
```js
$(...).css({fontFamily: 'serif'})
// OR
$(...).css({
    fontFamily: 'serif',
    color: '#e1e7e6',
    display: flex
})
```

## Toggle Class

Cara yang disarankan, yaitu dengan cara membuat sebuah class baru dalam CSS lalu toggle class tersebut.

```css
.toggle-btn-style {
  background-color: red;
  outline-color: red;
}
```
```js
let $initVal = $(".demo-btn").html()
$(".demo-btn").on("mousedown", (event)=>{
    $(event.currentTarget).html("Keep holding!!!")
    .addClass('toggle-btn-style') // Method to change add class
}).on("mouseup", (event)=>{
    $(event.currentTarget).html($initVal)
    .removeClass('toggle-btn-style') // Method to change remove class
})
```

Hasilnya tetap sama namun styling diatur didalam CSS agar tetap terorganisir. Untuk variasi toggle, gunakan `.toggleClass()`.

## Animate

Membuat animasi transisi properti CSS, penggunaan sama seperti `.css()`.
```js
let $initVal = $(".demo-btn").html()
$(".demo-btn").on("mousedown", (event)=>{
    $(event.currentTarget).html("Keep holding!!!")
    .addClass('toggle-btn-style')
    .animate({fontSize: '1.8rem'}, 200) // Method to animate
}).on("mouseup", (event)=>{
    $(event.currentTarget).html($initVal)
    .removeClass('toggle-btn-style')
    .animate({fontSize: '1.5rem'}, 200) // Method to animate
})
```

![jQuery Demo](/jquery/2023-10-25-jquery-4/gif2.gif)

Properti yang bisa di animate terbatas pada properti yang memiliki numeric value seperti `font-size`, `margin`, `padding` dan yang memiliki satuan seperti `px` atau `rem` dan lainnya.