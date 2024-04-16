+++
title = "Javascript Regex 03"
draft = false
weight = 3
tags = ['javascript']
+++

## Wildcard II

Di halaman ini kita akan membahas wildcard `?`, `*`, `+` dan `{}`

### { }

Artinya adalah sebuah range untuk huruf sebelumnya: 

```plain
/r{2,4}/gi
```
Diatas mencari huruf "r" (global, case-insensitive) yang berdempetan minimal 2 buah dan maksimal 4 buah.

```js
"arr ar arr a arrr arrrrr arrraraarrrrrarr".match(/r{2,4}/gi)
// Hasil log
// a|rr| ar a|rr| a a|rrr| a|rrrr|r a|rrr|ara|rrrr|ra|rr|
[ 'rr', 'rr', 'rrr', 'rrrr', 'rrr', 'rrrr', 'rr' ]
```

Jika koma tidak ada, maka karakter maksimal sama dngan minimum

```js
"arr ar arr a arrr arrrrr arrraraarrrrrarr".match(/r{4}/gi)
// Hasil log
// arr ar arr a arrr a|rrrr|r arrrara|rrrr|rarr
[ 'rrrr', 'rrrr' ]
```

### ?

`?` sama dengan `{0,1}`, `?` merupakan syntax sugar dari `{}`.

```js
var s="ab";
console.log( /a?b/.test(s) );  //output: true--it matches 1"a" and 1"b"("ab")
console.log( /x?b/.test(s) );  //output: true--it matches 0"x" and 1"b"("b")
console.log( /x?b?/.test(s) ); //output: true--it matches 0"x" and 1"b"("b")
console.log( /x?y?/.test(s) ); //output: true--it matches 0"x" and 0"y"("")
```

### *

`*` sama dengan `{0, infinity}` menangkap 0 sampai tidak terbatas karakter.

```js
var s="aaaabbbb";
console.log( s.match(/a*b/) + "" );  //output: aaaab
console.log( s.match(/a*b*/) + "" ); //output: aaaabbbb
```

### +

`+` sama dengan `{1, infinity}` menangkap 1 sampai tidak terbatas karakter.

```js
var s="aaaabbbb";
console.log( s.match(/a+b/)+"" );  //output: aaaab
console.log( s.match(/a+b+/)+"" ); //output: aaaabbbb
console.log( s.match(/ab+/)+"" );  //output: abbbb
console.log( s.match(/x+b+/)+"" ); //output: null  (it matches at least 1 "x")
```