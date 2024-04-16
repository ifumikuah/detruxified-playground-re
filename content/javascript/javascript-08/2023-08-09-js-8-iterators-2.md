+++
title = "Javascript 08: forEach"
draft = false
weight = 2
tags = ['javascript']
+++

# forEach()

Alternatif dari listing array menggunakan for loop, forEach menawarkan kode yang lebih singkat menggunakan callback functions.

```js
const animals = ["Panda","Kangaroo","Lion","Cat","Owl","Eagle"];

animals.forEach(function (iterateAnimals) {
    console.log(`It's a ${iterateAnimals}`);
});
```
```plain
It's a Panda
It's a Kangaroo
It's a Lion
It's a Cat
It's a Owl
It's a Eagle
```

Fungsi bisa disederhanakan menggunakan arrow functions dan implicit return.

```js
...
animals.forEach(iterateAnimals => console.log(`It's a ${iterateAnimals}`));
```

# Note

`.forEach()` akan selalu mengeluarkan `undefined` jika dipanggil/sebagai callback.