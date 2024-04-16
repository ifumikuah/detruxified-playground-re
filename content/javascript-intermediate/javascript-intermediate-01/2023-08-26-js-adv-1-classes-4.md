+++
title = "Javascript Intermediate 01: Inheritance II"
draft = false
weight = 4
tags = ['javascript']
+++

Membuat Superclass atau parent class.

```js
class Animal {
    constructor(name,mobility){
        this._name = name;
        this.mobility = mobility;
    }
    get name(){
        return this._name;
    }
    get mobility(){
        return this.mobility;
    }
}; 
```
Diatas adalah superclass basic yang akan digunakan untuk tutorial Inheritance selanjutnya. Superclass ini merepresentasikan binatang sebagai parent-class dan child-class yang akan datang sebagai jenis binatang seperti ular, kuda, dan burung.

## Sub-class

### Horse

Properti:
- Inherited: `name`,`mobility`
- Own: N/A
- Method: `echo`<sup>1</sup>,`hoofDamage`

### Bird

Properti:
- Inherited: `name`,`mobility`
- Own: `altitude`,`fly`
- Method: `echo`<sup>1</sup>,`weather`

<sup>[1]</sup> Inherited from Parent-class

## Superclass

```js
class Animal {
    constructor(name,mobility){
        this._name = name;
        this._mobility = mobility;
    }
    get name(){
        return this._name;
    }
    get mobility(){
        return this._mobility;
    }
    echo(words){
        console.log(`${this._mobility} says ${words}`);
    }
}; 
```