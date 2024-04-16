+++
title = "Javascript 03: Ternary"
draft = false
weight = 7
tags = ['javascript']
+++


### Sinopsis

```js
const hungry = true

hungry ? console.log("eat!")
: console.log("do workout!");
```

### Details

Ternary operator, `?` membuka operasi ternary, jika `true` maka block pertama sebelum `:` akan dieksekusi, jika `false` maka block terakhir (sesudah `:`) akan dieksekusi

```js
let isCorrect = true;

isCorrect ? console.log('Correct!')
: console.log('Incorrect!');

let favoritePhrase = 'Love That!';

favoritePhrase === 'Love That!' ? console.log('I love that!')
: console.log("I don't love that!");
```
Output
```plain
Correct!
I love that!
```