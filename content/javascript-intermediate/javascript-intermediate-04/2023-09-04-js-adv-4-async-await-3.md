+++
title = "Javascript Intermediate 04: await II"
draft = false
weight = 2
tags = ['javascript']
+++

## await yang bergantung

Await chaining memiliki cara kerja yang sama dengan `.then()` chaining.

```js
const count = async () => {
    const a = await one();
    const b = await two(a);
    const c = await three(b);
    console.log(c);
}
```
Diatas, `b` dan `c` bergantung dari Promises sebelumnya. Jadi, ketika `c` di trigger, `b` akan ketrigger dan `b` akan mentrigger `a`.

Output:
```plain
one
two
three
```

### Full Code
```js
const one = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log("one");
            resolve ("one");
        }, 500);
    })
}

const two = (one) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (one) {
                console.log("two");
                resolve ("two");
            }
        }, 500);
    })
}

const three = (two) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (two) {
                resolve ("three");
            }
        }, 500);
    })
}

const count = async () => {
    const a = await one();
    const b = await two(a);
    const c = await three(b);
    console.log(c);
}

count();
```