+++
title = "Javascript Intermediate 01: Classes"
draft = false
weight = 1
tags = ['javascript']
+++

Membuat class, berguna untuk membuat objek dengan properti yang sama dengan cepat.

## Overview
```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

const cat = new Animal('Cat');
cat.speak();
```

## Constructor

`constructor()` dipanggil setiap saat ingin membuat class baru.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
};
```
- `Animal` adalah nama class, umumnya nama class memiliki nama dalam PascalCase.

{{< expand "Apa itu PascalCase" "🤔" >}}
## PascalCase

Sebuah penamaan yang dimulai dengan huruf kapital di setiap awal huruf dari kata.\
Contoh: `KudaLaut`, `HargaBarangLama`, `Kucing`

Biasanya digunakan untuk mendefinisikan sebuah nama class dalam bahasa pemrograman OOP.
{{< /expand >}}

- JavaScript akan mentrigger `constructor()` setiap saat ingin membuat instance baru dari `Animal`.
- `constructor` menerima satu argument, `name` sebagai parameter.
- `this.` digunakan untuk definisikan properti `this.name` sebagai key dari argument `name`.

## Instance

Instance atau instansi, adalah sebuah object yang mengandung property dari class sebagai propertinya.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
};

const whale = new Animal("Humpback Whale");
console.log(whale.name); // Humpback Whale
```
Membuat object bernama `whale`, dengan property `name` Humpback Whale.

## Methods

Sama seperti object, class juga memiliki methods yang sifatnya mirip dengan object methods.

```js
class Animal {
    constructor(name) {
      this.name = name;
    }
    echo(words){
      return `${this.name} says "${words}"`;
    }
};

const whale = new Animal("Humpback Whale");
console.log(whale.echo("Hello World!"));
```
```plain
Humpback Whale says "Hello World!"
```
{{< hint type=info >}}
Berbeda dengan object, methods tidak dipisah oleh comma `,` dengan methods lainnya
{{< /hint >}}