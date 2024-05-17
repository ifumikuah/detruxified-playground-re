+++
title = "NaN"
draft = false
weight = 8
tags = ['javascript']
+++

**Not a Number**, adalah nilai numerik. Artinya `NaN` adalah sebuah angka atau termasuk kedalam tipe data numerik `number`.

```js
console.log(typeof NaN); // 'number'
```

Jadi, apakah `NaN` sama dengan desimal pada umumnya misal: `92`?

**Jawabannya**, tidak secara nilai/value namun ya secara tipe data.

```js
console.log(typeof NaN === typeof 92); // 'true'
```

`NaN` adalah value dari tipe data `number` untuk `number` yang tidak valid sebagai hasil evaluasi.

## Apa syarat untuk menjadi NaN ?

Harus menjadi evaluasi tidak valid dari sebuah perhitungan.

```js
const eval = 92 - "two";
console.log(eval); //NaN
```

Walaupun `NaN` artinya bukan angka, hal ini bukan berarti `string` termasuk kedalam `NaN`.

```js
console.log(Number.isNaN("cow")) //false
console.log(Number.isNaN(0/0)) //true
```

