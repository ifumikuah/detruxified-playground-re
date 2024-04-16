+++
title = "Javascript 01: Tipe Data"
draft = false
weight = 3
tags = ['javascript']
+++

Ada tujuh tipe data di javascript, yaitu :

- *Number*, Semua angka termasuk desimal `3,14`,`1`,`57`,`3500`

- *String*, Kumpulan semua karakter termasuk angka yang dikurung dalam petik `""`/`''`, contoh `"Ikan"`,`'69420'`

- *Boolean*, Hanya memiliki 2 nilai yaitu `True` dan `False`

- *Null*, Tipe data yang nilainya belum ditentukan, bernilai `null`

- *Undefined*, Tipe data yang nilainya tidak ada, bernilai `undefined`

- *Symbol*, Jenis data di versi baru, sangat jarang digunakan untuk sehari-hari

- *Object*, kumpulan beberapa data

Enam secara berturut merupakan jenis data primitif, sedangkan *Object* termasuk data kompleks.

Untuk membedakan antara `Null` dan `Undefined`, cukup ingat bahwa `Null` harus diberikan secara *eksplisit* sebaliknya dengan `Undefined`.

Jika tidak memasukkan nilai apapun dalam sebuah variabel, maka hasilnya otomatis `undefined`

```js
let myVar;
console.log(myVar);

let yourVar = null;
console.log(yourVar);
```

Output

```js
undefined
null
```