+++
title = "Javascript 08: High Order Functions"
draft = false
weight = 1
tags = ['javascript']
+++

Function temasuk first-class object di javascript, ini artinya function memiliki sifat yang sama dengan data types dan variable.

High-order functions adalah jenis fungsi yang bisa memanggil fungsi lain didalamnya.

```js
function talkTo(person,me) {
    console.log(`You decided to talk with ${person()}`);
    console.log(`${me} : Good Morning!, ${person()}`);
}

function robert() {
    return "robert";
}

function lisa() {
    return "lisa";
}

talkTo(lisa,"Daniel");
```

- Fungsi `talkTo(person,me)` adalah *high-order* functions yang bisa memanggil fungsi lain di argument/parameter nya.

- Fungsi `lisa()` dan `robert()` adalah *callback* function, fungsi ini bersedia dipanggil oleh `talkTo`.

### Contoh lain

```js
function buyGifts(goods,quantity) {
    console.log(`You just bought ${quantity} ${goods()}`);
}

function fruits () {
    const fruit = ['apple', 'strawberry', 'orange', 'mango'];
    const rand = fruit[Math.floor(Math.random() * fruit.length)];
    return rand;
}

function electronic () {
    const items = ['iphone', 'laptop', 'console', 'smartwatch'];
    const rand = items[Math.floor(Math.random() * items.length)];
    return rand;
}

buyGifts(electronic,5);
```
`buyGifts` akan mencetak barang berjenis buah atau elektronik secara random yang baru saja kamu beli.