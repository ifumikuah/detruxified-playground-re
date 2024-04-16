+++
title = "Javascript Intermediate 01: Static Method"
draft = false
weight = 7
tags = ['javascript']
+++

Static method adalah method yang dipanggil langsung dari Superclass, dengan kata lain method ini tidak perlu membuat instance ketika dipanggil.

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
        console.log(`${this._name} says ${words}`);
    }
    static generateName(){
        const nameArray = ["Bob","Jack","Pearl","Bale","Rose","Andrew","Diana"];
        return nameArray[Math.floor(Math.random() * nameArray.length)]; 
    }
};

console.log(Animal.generateName());
```
```
Nama acak sesuai dengan array `nameArray`
```