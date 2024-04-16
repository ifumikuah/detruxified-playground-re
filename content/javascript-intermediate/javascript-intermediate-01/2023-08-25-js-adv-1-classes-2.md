+++
title = "Javascript Intermediate 01: Method calls"
draft = false
weight = 2
tags = ['javascript']
+++

Memanipulasi data yang ada di classes dengan method.

## Overview

```js
class Animal {
    constructor(name) {
      this._name = name;
      this._mobility = 100;
    }
    get name(){
      return this._name;
    }
    get mobility(){
      return this._mobility;
    }
    decMobility(num){
      this._mobility -= num;
    }
};
```
Dengan memanggil `decMobility()`, akan mengurangi `this._mobility` sebesar `num`.

## Pemanggilan

```js
// Class codes above

const whale = new Animal("Humpback Whale");
whale.decMobility(40);

console.log(whale.mobility);
```
```plain
60
```
`whale.mobility` adalah sebuah get method yang akan return hasil dari `this._mobility` untuk `whale`