+++
title = "Javascript Intermediate 04: await Promises.all()"
draft = false
weight = 5
tags = ['javascript']
+++

Menjalankan semua promises secara parallel.

```js
const rutinities = async () => {
    const x = await Promise.all([cleanDish(),washClothes(),takeShower()])
    console.log(`${x[0]} \n${x[1]} \n${x[2]}`);
}
```
Akan menjalankan tiga Promises secara bersamaan.
```js
console.log(`${x[0]} \n${x[1]} \n${x[2]}`);
```
`console.log` akan mencetak hasil setiap Promises di garis baru.

## The Promises

```js
function time() {
    return Math.floor(Math.random()*4000); // Generate random time upto 4s
}

const delay = time();

const cleanDish = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const ready = "Cleaned Dish: OK"
            resolve(ready)
        }, delay);
    })
}

const washClothes = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const ready = "Washed Clothes: OK"
            resolve(ready)
        }, delay);
    })
}

const takeShower = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const ready = "Take a Shower: OK"
            resolve(ready)
        }, delay);
    })
}
```