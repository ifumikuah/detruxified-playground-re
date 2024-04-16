+++
title = "Javascript Regex 02"
draft = false
weight = 2
tags = ['javascript']
+++

## Wildcard

Sebuah Wildcard biasanya ditandai dengan simbol, wildcard pertama adalah `.`.

`.` memilih sebuah karakter **apa saja**.

```js
console.log( "abcdef".match(/./g) )   //output: [ 'a', 'b', 'c', 'd', 'e', 'f' ]
console.log( "abcdef".match(/../g) )  //output: [ 'ab', 'cd', 'ef' ]
console.log( "abcdef".match(/.../g) ) //output: [ 'abc', 'def' ]
```

### ^ and $

`^` mencari yang cocok di awal, sedangkan `$` adalah kebalikannya.

```js
var str="abcdef";
console.log( str.match(/^../g) )  // [ 'ab' ]
console.log( str.match(/..$/g) )  // [ 'ef' ]
```

Kita bisa menggabungkannya di kasus jika ingin mencari sebuah kata dengan limit karakter.

```js
// Mencari kata dengan batas 4 karakter
console.log( "abcd".match(/^....$/g) )  // [ 'abcd' ]
console.log( "abc".match(/^....$/g) )  // null
```