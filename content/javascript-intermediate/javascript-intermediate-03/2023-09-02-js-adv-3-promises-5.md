+++
title = "Javascript Intermediate 03: Chaining"
draft = false
weight = 5
tags = ['javascript']
+++

Handlers hanya memproses dua kondisi yaitu *fulfilled* dan *rejection*.

```js
const myAge = (age) => {    
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (age >= 18) {
                resolve("Age Approved")
            } else {
                reject("Age Declined")
            }
        }, 500);
    })
}

myAge(19)
    .then((val)=>{
        console.log(val);
    })
    .catch((val)=>{
        console.log(val);
    })
```

Logika diatas bisa dibuat menjadi lebih kompleks, dengan *chaining*.

## Composition

Contohnya, jika `myAge` berstatus *fulfilled*, mungkin kita bisa meneruskan tahap selanjutnya, yaitu verifikasi negara.

Pertama, kita perlu revisi code kita dengan memberi sebuah object sebagai input.

```js
const miguel = {
    name: "Miguel Venerandi",
    age: 14,
    country: "Venezuela"
}
```
Disini, `myAge()` akan menerima object `miguel` sebagai parameter, membuat semuanya lebih terstruktur. Yang kita butuhkan adalah verifikasi negara jika Miguel diatas 18 tahun. Jika tidak, maka Miguel akan langsung gagal di step verifikasi umur.

### Main functions for compositions

```js
const {randomizer} = require('./randomGenerator/randomCodeGenerator.js'); // Fungsi untuk generate kode
const randomDelay = Math.floor(Math.random() * 1000); // Generate waktu random 0 - 0.9 ms

const myAge = (person) => {    
    age = person.age;
    username = person.name;
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (age >= 18) {
                resolve(person)
                console.log(`Confirmed ${username} at ${age} years old`)
            } else {
                reject("Age Declined")
            }
        }, randomDelay);
    })
}

const myCountry = (person) => {
    country = person.country;
    excludeCountry = ["Saudi Arabia","Iran","Vatican","North Korea"];
    isCountryMatch = excludeCountry.includes(country);
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (!isCountryMatch) {
                resolve(`Connecting ${person.name} from ${country}`);
            } else {
                reject("Sorry, It's look like your country was under our visitor ban list")
            }
        }, randomDelay);
    })
}
```

Sebagai acuan untuk fungsi sesudahnya, fungsi pertama atau sebelumya harus resolve object ataupun sesuatu agar bisa dipakai oleh fungsi berikutnya sebagai argument.

## Chaining compositions

```js
myAge(miguel)
    .then((val)=>{
        return myCountry(val)
    })
    .then((val)=>{
        console.log(val);
    })
    .catch((val)=>{
        console.log(val);
    })
```
Kita fokus terhadap dua Handler `.then()`.

### .then() pertama

`.then()` pertama akan `return` fungsi `myCountry()` yang tugasnya sebagai verifikasi negara. Jika umur Miguel diatas 18, maka `myCountry()` akan dieksekusi.

### .then() kedua

`.then()` kedua akan mengeksekusi fungsi `myCountry()` dan mencetak isi didalam fungsi resolve nya.