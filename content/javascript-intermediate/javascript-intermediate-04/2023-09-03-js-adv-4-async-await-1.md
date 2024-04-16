+++
title = "Javascript Intermediate 04: async"
draft = false
weight = 1
tags = ['javascript']
+++

## Syntactic sugar

Syntactic sugar adalah sintaks yang tidak ada tambahan maupun pengurangan difiturnya, sintaks ini semata hanya untuk improvisasi *readibility* dari kode, layaknya gula sebagai pemanis.

## async

Async adalah syntactic sugar dari Promises.

## Promises vs async

Promises:
```js
function withConstructor(num){
  return new Promise((resolve, reject) => {
    if (num === 0){
      resolve('zero');
    } else {
      resolve('not zero');
    }
  });
}
```
async:
```js
async function withConstructor(num){
    if (num === 0){
        return('zero');
    } else {
        return('not zero')
    }
}
```

Dikarenakan async adalah syntactic sugar dari Promises, keduanya kompatible satu sama lain.

```js
withAsync(100)
  .then((resolveValue) => {
  console.log(` withAsync(100) returned a promise which resolved to: ${resolveValue}.`);
})
```
```plain
not zero
```