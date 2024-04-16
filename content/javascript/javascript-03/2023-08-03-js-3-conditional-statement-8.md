+++
title = "Javascript 03: Else If"
draft = false
weight = 8
tags = ['javascript']
+++

### Sinopsis

```js
if () {

} else if () {

} else if () {

} else {

}

```

### Details

Else if memungkinkan kamu untuk menghasilkan kondisi dengan pilihan/outcome lebih bervariasi.

```js
let season = 'fall';

if (season === 'spring') {
  console.log('It\'s spring! The trees are budding!');
} else if (season === 'winter') {
  console.log('It\'s winter! Everything is covered in snow.');
} else if (season === 'fall') {
  console.log('It\'s fall! Leaves are falling!');
} else if (season === 'summer') {
  console.log('It\'s sunny and warm because it\'s summer!');
} else {
  console.log('Invalid season.');
}
```
Output
```plain
It's fall! Leaves are falling!
```

