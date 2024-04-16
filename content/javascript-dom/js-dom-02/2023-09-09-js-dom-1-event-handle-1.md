+++
title = "Event Handle: Event Listener"
draft = false
weight = 1
tags = ['javascript','html']
+++

Event Listener "menyalakan"/trigger sebuah fungsi `x` disaat user `y` sebuah `z`.

```js
// Syntax Synopsis
const z = document.getElementById('red-button');
function x (){
    z.style.display = 'none';
}
z.addEventListener('y',z);
```

`'y'` adalah kumpulan string event type bawaan dari javascript, salah satunya adalah `'click'`, menyalakan fungsi `x` jika user mengklik tombol `z`.

Ganti `'y'` dengan event type yang diinginkan, referensi event type bisa dilihat [disini](https://www.w3schools.com/jsref/dom_obj_event.asp).

## On Event

Selain `.addEventListener()`, ada cara lain untuk trigger sebuah event, `onevent` memiliki cara kerja hampir serupa.
```js
//Syntax Synopsis
const z = document.getElementById('red-button');
function x (){
    z.style.display = 'none';
}
z.onY = x
```
Sekali lagi, ubah `Y` menjadi event type, tapi tambahkan `on` diawalan, e.g `z.onclick = x` akan trigger event `x` jika `z` di klik.

`onevent` boleh dipakai tapi lebih dianjurkan untuk menggunakan `.addEventListener()`.