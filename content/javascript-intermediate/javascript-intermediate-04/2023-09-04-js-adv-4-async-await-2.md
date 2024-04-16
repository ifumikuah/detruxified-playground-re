+++
title = "Javascript Intermediate 04: await"
draft = false
weight = 2
tags = ['javascript']
+++

`await` adalah keyword yang hanya bisa digunakan dengan `async`. `await` akan *halt* eksekusi dan menunggu Promise *resolved*/*rejected*.

```js
const counting = async () => {
    console.log("one");
    const x = await count();
    console.log(x);
    console.log("three");
}
```
`console.log(x)` akan menunggu jawaban dari fungsi dibawah ini sebelum lanjut ke `console.log("three")`
```js
const count = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("two");
        }, 1000);
    })
}
```
Jika dieksekusi fungsi pertama tadi:
```js
counting()
```
```plain
one
two
three
```