+++
title = "Javascript Additions: Map"
draft = false
weight = 4
tags = ['javascript']
+++

Object `Map` adalah object iterable yang mirip dengan *object*. Berbeda dengan object, map hanya bisa di definisikan melalui constructor.

```js
const personObject = {
  nama: "Richard",
  umur: 42,
  pekerjaan: "Dokter", 
}
```
```js
const personMap = new Map();

personMap.set("nama", "Richard");
personMap.set("umur", 42);
personMap.set("pekerjaan", "Dokter");
```

Cobalah untuk log `personMap`:

```plain
Map(3) { 'nama' => 'Richard', 'umur' => 42, 'pekerjaan' => 'Dokter' }
```

Maka map juga mencetak sepasang key-value sama halnya seperti object.

Bedanya, key pada map dapat menampung tipe data apapun, beda dengan object yang terbatas pada string dan symbol.

## Mengakses value

Panjang map bisa didapat dari `Map.prototype.size`:

```js
console.log(personMap.size); // 3
```

Sedangkan value dan key dapat diakses melalui 2 cara:

### for of loop

```js
for (const [key, val] of personMap) {
  console.log(`${key} => ${val}`);
}
```

Perlu diingat bahwa urutan pada `[key, val]` adalah `key` terdahulu, lalu `val` sebagai value.

### forEach

Untuk forEach, looping ini akan return value terdahulu kemudian key, kebalikan dari `for of` loop.

```js
personMap.forEach((val, key) => {
  console.log(`${key} => ${val}`);
})
```

### Map.prototype.get()

`Map.prototype.get()` sama halnya seperti `Object.value`, Method ini akan return value dari key yang ingin dicari.

```js
const nama = personMap.get("nama")
console.log(nama) // Richard
```

## Lainnya

Mengecek kehadiran key dalam suatu map:

```js
console.log(personMap.has("kelamin")) // false
```

Menghapus key beserta valuenya:

```js
console.log(personMap.delete("pekerjaan"))
console.log(personMap.has("pekerjaan")) // false
```
