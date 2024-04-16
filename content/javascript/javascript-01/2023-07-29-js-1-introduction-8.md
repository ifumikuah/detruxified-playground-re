+++
title = "Javascript 01: Object and Methods"
draft = false
weight = 8
tags = ['javascript']
+++


### Synopsis

```js
object.theMethod();
```

### Details

```js
console.log();
```

Diatas merupakan salah satu object. `console` sebagai objek dan `log` sebagai metode.

### contoh lain : [Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

```js
Math.floor(10.6);
```

*method* `floor` akan membulatkan 10.6 menjadi 11

beberapa *object* bisa dikurung didalam *object* lainnya

```js
console.log(Math.floor(5.8));
```
Output
```cmd
6
```

atau, print bilangan desimal acak diantara 0 sampai 1 yang dikalikan dengan 10 
```js
console.log(Math.floor(Math.random()*10));
```
`Math.random` menghasilkan desimal acak diatara 0 sampai 1, output bisa jadi 0, 1 atau nol koma 1 sampai 9