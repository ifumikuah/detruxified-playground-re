+++
title = "Javascript 03: Logical Operator"
draft = false
weight = 4
tags = ['javascript']
+++


### Sinopsis

```js
if ( condition1 && condition2 ) {
    do.something();
} else {
    do.other();
}
```

### Details

Operator logika, ada tiga operator yaitu `&&`, `||` dan `!`. Sangat berguna untuk mem-*filter* dua kondisi atau lebih.

`&&`, *and* operator, hasil akan `true` jika kedua kondisi bernilai `true`.

`||`, *or* operator, hasil akan `true` jika salah satu kondisi bernilai `true`.

`!`, *not* operator, mengeluarkan hasil yang berlawanan.

```js
let mood = 'sleepy';
let tirednessLevel = 6;

if (mood === 'sleepy' !! tirednessLevel > 8 ) {
  console.log('time to sleep');
} else {
  console.log('not bed time yet');
}
```
Output
```plain
time to sleep
```

```js
let sleepy = false;
console.log(!sleepy);
```
Output
```plain
true
```

