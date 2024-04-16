+++
title = "Event Handle: Event Listener II"
draft = false
weight = 2
tags = ['javascript','html']
+++

## Stop Listener

`.removeEventListener()` akan membuat target berhenti 'listening', artinya fungsi listener target akan mati sampai di refresh page.

```js
target.removeEventListener('click', func);
```
Diatas akan mematikan fungsi `func` dan 'listening' dari `target` jika di klik.

```js
//Detailed Example
const target = document.getElementById('red-button');
function func (){
    target.style.backgroundColor = 'cyan';
    target.removeEventListener('click', func);
}

target.addEventListener('click',func);
```

Klik tombol `target` akan mentrigger `func` sekaligus membuat `target` dalam keadaan 'mati'.