+++
title = "jQuery: Intro"
draft = false
weight = 1
tags = ['javascript']
+++

jQuery adalah library javascript terkenal dan *legend* untuk memudahkan DOM di javascript.

## Acquire jQuery

Untuk bisa menggunakan jQuery, kamu harus *include* jQuery di html/web kamu. Salah satu cara tercepat adalah dengan menggunakan CDN:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
```

## Syntax

Gunakan `$` untuk mengakses jQuery, dan basic syntax nya seperti ini:

```js
$(selector).action()
```

## Getting started

```js
$(document).ready(function(){

  // codes

});
```

Diatas akan menjalankan semua yang ada di `codes` saat document/page *fully loaded*.

### Demo

```js
$(document).ready(function(){
    $("#demo-btn").click(()=>{
        $(".text-box").toggle()
    })
})
```
```html
<button class="btn" id="demo-btn">Freedom Starts Here</button>
<div class="text-box hide">
    <p class="text">Sadly, there's no freedom for you.</p>
    <p class="emoji">😟</p>
</div>
```
![jQuery Demo](/jquery/2023-10-23-jquery-1/gif1.gif)

Saat, di klik akan *toggle* bacaan dan emoji dibawahnya. Sama seperti DOM di JS Vanilla, dengan jQuery kita bisa membuat kode yang lebih pendek dan readable.