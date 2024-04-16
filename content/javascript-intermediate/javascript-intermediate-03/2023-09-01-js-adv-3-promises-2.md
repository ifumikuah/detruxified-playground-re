+++
title = "Javascript Intermediate 03: Promises I"
draft = false
weight = 2
tags = ['javascript']
+++

## Membuat promises

```js
const executorFunction = (resolve, reject) => {
 if (desiredCondition) {
     resolve('I resolved!');
 } else {
     reject('I rejected!'); 
 }
}
const myFirstPromise = new Promise(executorFunction);
```
Lihat `Promise`:\
`new Promise` adalah constructor untuk membuat sebuah promises.

`Promise` meminta satu parameter, yaitu sebuah fungsi `executorFunction`, atau disebut juga *executor*

## Executor

```js
const executorFunction = (resolve, reject) => {
 if (desiredCondition) {
     resolve('I resolved!');
 } else {
     reject('I rejected!'); 
 }
}
```
Executor memiliki dua parameter fungsi, yaitu `resolve()` dan `reject()`. Dua fungsi ini sebenarnya bawaan dari javascript, tapi bisa diubah namanya sesuka hati.

### resolve()
```js
if (desiredCondition) {
     resolve('I resolved!');
 }
```
Seperti yang dibilang tadi, `resolve()` harus diberi satu argument. Ketika di-invokasi/invoked, kondisi *pending* promise akan menjadi *fulfilled*.

### reject()
```js
else {
     reject('I rejected!'); 
 }
```
Sifatanya sama seperti `resolve()`, `reject()` akan membuat kondisi *pending*  menjadi *rejected*.

