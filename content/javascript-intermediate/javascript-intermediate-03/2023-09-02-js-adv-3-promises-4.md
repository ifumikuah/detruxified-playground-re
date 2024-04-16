+++
title = "Javascript Intermediate 03: Handler"
draft = false
weight = 4
tags = ['javascript']
+++

## Handler

```js
const pizzaIsAvailable = true;

const executor = (pass,fail) => {
    setTimeout(() => {
        if (pizzaIsAvailable) {
            pass("Pizza is Available!")
        } else {
            fail("Pizza is out of stock!")
        }
    },1500);
}

const aPromise = new Promise(executor);
console.log(aPromise);
```

Kode diatas sudah fungsional jika dijalankan, tetapi tidak bisa diobservasi dengan `console.log()` tradisional, dikarenakan sekali lagi, berjalan secara asynchronous.

{{< hint type=info >}}
Kamu masih bisa log dengan `console.log(aPromise);` tetapi tidak ada yang muncul saat *fulfilled* dan sebuah pesan error muncul saat *rejected*  (normal behavior).
{{< /hint >}}

Sebuah handler dibutuhkan untuk menangani hal ini, tapi sebelum itu, fungsi promise tadi dan sebelumnya harus di sederhanakan dan dipersingkat.

## Refactor

Ingat, construtor promises hanya menerima sebuah callback function sebagai parameter atau disebut juga *executor*. callback tersebut bisa disederhanakan dengan hanya membuat sebuah anonymous function langsung sebagai argumentnya.

```js
const aPromise = new Promise((pass,fail) => {
    setTimeout(() => {
        if (pizzaIsAvailable) {
            pass("Pizza is Available!");
        } else {
            fail("Pizza is out of stock!");
        }
    },1500)
});
```
Atau, ingin membuat sebuah promise didalam sebuah fungsi autentikasi umur: 

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
```

## Cara membuat Handler

Pertama, buat dua fungsi sebagai fungsi callback untuk kedua kondisi.

```js
const approved = (val) => {
    console.log(val);
}

const disapproved = (val) => {
    console.log(val);
}
```

Parameter `val` akan otomatis return value dari parameter resolve atau reject, `"Age Approved"` atau `"Age Declined"`

## .then()

Method `.then()` digunakan sebagai Handler kondisi dari `myAge()`.

```js
myAge(18).then(approved,disapproved);
```

`.then()` hanya menerima dua parameter fungsi callback, parameter pertama untuk kondisi *fulfilled* dan kedua untuk *rejected*

## In Action

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

const approved = (val) => {
    console.log(val);
}

const disapproved = (val) => {
    console.log(val);
}

myAge(12).then(approved,disapproved);
```
```js
Age Declined
```

### Refactor

Sama seperti sebelumya, callback function dapat di persingkat dengan langsung membuat anonymous function didalam parameternya.

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

myAge(12)
    .then((val)=>{
        console.log(val);
    },(val)=>{
        console.log(val);
    });
```

## .catch()

`.catch()` berfungsi untuk meng-handle sebatas *rejection*. `.catch()` hanya menerima satu parameter, yaitu sebuah callback function untuk *rejected*.

```js
myAge(12)
    .then((val)=>{
        console.log(val);
    })
    .catch((val)=>{
        console.log(val);
    })
```
Diatas akan memiliki hasil yang sama dengan sebelumnya.