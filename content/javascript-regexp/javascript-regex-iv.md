+++
title = "Javascript Regex 04"
draft = false
weight = 4
tags = ['javascript']
+++

## Wildcard IV

Di halaman ini kita akan membahas wildcard `|`, `[]`,dan `()`.

### |

`|` sama seperti logika `or`, memilih *atau*, memilih antara dua atau lebih seleksi.

```js
var str="abc";
console.log( str.match(/a|b/g) );    //output: [ 'a', 'b' ]
console.log( str.match(/a|b|c/g) );  //output: [ 'a', 'b', 'c' ]
```

### ()

`()` adalah nesting, ini memperbolehkan kamu nesting seleksi, membuat seleksi lebih spesifik dan kompleks.

```js
var str="cat bat hat";
console.log( str.match(/(c|b|h)at/g) );  //output: [ 'cat', 'bat', 'hat' ]
```
Regexp diatas sama dengan:
```js
/cat|bat|hat/g
```

Nesting bisa dikombinasi dengan `?`, `*` dan `+`.

```js
var str="ababcdcd";
console.log( str.match(/(ab)*/g) );    //output: [ 'abab', '', '', '', '', '' ]
console.log( str.match(/(ab)+/g) );    //output: [ 'abab' ]
console.log( str.match(/(ab)?(cd)*/g) );  //output: [ 'ab', 'abcdcd', '' ]
console.log( str.match(/(ab)?(cd)+/g) );  //output: [ 'abcdcd' ]
```

### []

`[]` artinya range, membuat sebuah range 0 sampai 9 dengan `[0-9]` sebaliknya juga `[a-z]` membuat range a sampai z (lowercase)

Dibawah ini fungsi untuk mengecek `username`:
```js
const usercheck = (username) => new RegExp(/^[a-zA-Z][a-zA-Z0-9_]{6,12}$/).test(username)
```

Jika kamu menambahkan `^` didalam `[]`, maka kamu membuat sebuah seleksi invers

```js
var str="a1!b2@c3#d4$e5%";
console.log( str.replace(/[^a-z]/g,""))  //output: abcde
```

Diatas, mengkosongkan semua karakter kecuali a sampai z.