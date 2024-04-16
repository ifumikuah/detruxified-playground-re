+++
title = "Javascript Intermediate 01: Inheritance III"
draft = false
weight = 5
tags = ['javascript']
+++

Membuat sub-class untuk burung dan kuda.

## Horse

```js
class Horse extends Animal {
    constructor(name,mobility){
        super(name,mobility);
    }
    hoofDamage(dmg){
        this._mobility -= dmg;
    }
}
```

Superclass `Animal` ada di post sebelumnya, membuat sub-class `Horse` dengan spesifikasi, sebagai berikut:

Properti:
- Inherited: `name`,`mobility`
- Own: N/A
- Method: `echo`,`hoofDamage`

`hoofDamage` adalah method khusus `Horse`. Cara kerjanya adalah output mobility - dmg ketika dipanggil.

```js
const arabianHorse = new Horse("Assad",100);
arabianHorse.hoofDamage(59)
console.log(arabianHorse.mobility);
```
```plain
41
```

## extends dan super

`extends` adalah key yang digunakan untuk deklarasi kalau, `Horse` merupakan sub-class dari `Animal`.

`super` digunakan untuk menandai, bahwa properti `name` dan `mobility` akan diambil berdasarkan `name` dan `mobility` yang ada di Superclass `Animal`.