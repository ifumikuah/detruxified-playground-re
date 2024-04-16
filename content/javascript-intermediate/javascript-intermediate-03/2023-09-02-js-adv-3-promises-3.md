+++
title = "Javascript Intermediate 03: Set timeout"
draft = false
weight = 3
tags = ['javascript']
+++

## setTimeout()

Dikarenakan promises berjalan diatas sesuatu yang asynchronous, kita membutuhkan sesuatu yang asynchronous juga.

`setTimeout()` adalah fungsi yang berjalan secara asynchronous.

`setTimeout()` meminta dua parameter, pertama sebuah fungsi callback dan kedua adalah delay yang ditentukan dalam miliseconds.

```js
setTimeout(()=>{
    console.log("This string runs asynchronous /w 2s delay")
},2000)
```

## setTimeout() berjalan didalam fungsi executor

```js
const executorFunction = (resolve, reject) => {
    setTimeout(() => {
        if (desiredCondition) {
            resolve('I resolved!');
        } else {
            reject('I rejected!'); 
        }
    },2000)
};
```