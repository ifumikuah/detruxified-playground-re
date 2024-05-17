+++
title = "Object Destructuring"
draft = false
weight = 10
tags = ['javascript']
+++

Destructuring sebuah object akan *dismantle* properti yang akan di-destructure menjadi value yang berbeda.

```js
let countobj = { num: 10 };
let { num } = countobj; // Membuat variabel baru `num`
```

Fenomena ini bisa di demonstrasikan sebagai bukti jika object yang di-destructure tidak terikat lagi dengan properti yang di-destructure didalamnya.

```js
let countobj = { num: 10 };
function inc({num}) {
  num++;
}

inc(countobj);
console.log(countobj); // 10
```

Sementara object yang dimanipulasi secara langsung objectnya akan tetap *lengket* value properti nya.

```js
let countobj = { num: 10 };
function inc(obj) {
  obj.num++;
}

inc(countobj);
console.log(countobj); // 11
```