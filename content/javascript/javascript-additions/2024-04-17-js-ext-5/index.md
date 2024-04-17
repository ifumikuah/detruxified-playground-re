+++
title = "Primitive & Non-Primitive References"
draft = false
weight = 4
tags = ['javascript']
+++

## Referensi Primitif

```js
var store = 12
var ref = store
```

Apakah diatas artinya `ref` adalah merujuk ke alamat yang sama dengan `store`?

Apakah `ref` dan `store` merujuk ke alamat `4F`?

**Tidak**, hal ini tidak berlaku untuk tipe data primitif: number, string dan boolean.

Ketika kamu membuat variable dengan referensi dari variable seperti diatas, yang kamu lakukan sebenarnya adalah: menduplikat nilai dari `store` untuk disimpan kedalam `ref`.

Jadi, kode diatas sama halnya seperti ini:

```js
var store = 12;
var ref = 12;
```

{{< hint type="info" title="Alasan Sebenarnya" >}}
Karena sebenarnya, ketika kamu menyimpan/assign data primitif kedalam sebuah variable. Variable tersebut memegang/menyimpan value tersebut secara langsung alih-alih mereferensikannya ke suatu alamat memori.
{{< /hint >}}

## Referensi Non-Primitif

Namun object dan array berkata lain. Ketika referensi dilakukan terhadap tipe data non-primitif seperti object dan array, mereka akan merujuk ke alamat memori yang satu.

{{< tabs "tab01" >}}
{{< tab  "Object" >}}
```js
const datum = {
  author: "Niccolo Machiavelli",
  title: "Il Principe",
};

const datumRef = datum;
datum.author = "Bertrand Russell";

console.log(datumRef); // { author: 'Bertrand Russell', title: 'Il Principe' }
```
{{< /tab >}}
{{< tab  "Array" >}}
```js
const array = ["Bread", "Rock", "Soil"];
const arrayRef = array;

array[1] = "Flint";
array.push("Sword");

console.log(arrayRef); // [ 'Bread', 'Flint', 'Soil', 'Sword' ]
```
{{< /tab >}}
{{< /tabs >}}

Ketika kamu assign non-primitif kedalam suatu variable, yang dilakukan sebenarnya adalah membuat referensi dari alamat memori yang menyimpan non-primitif tersebut.

Jadi, rujukan alamat memori tetap sama mau dimanapun dan oleh siapapun nilai non-primitif tersebut dirujuk.

## Summary

Tipe data primitif akan menyimpan langsung nilainya kedalam variable, berbeda dengan non-primitif yang membuat referensi ke suatu alamat memori.

Catatan diatas membantu memahami basic dari manajemen memori untuk membuat kode yang efisien. Catatan diatas juga bisa membantu sebelum belajar mengenai Garbage Collector (GC).