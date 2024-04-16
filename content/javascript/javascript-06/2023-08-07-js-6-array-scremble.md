+++
title = "Javascript 06: Array Scramble"
draft = false
weight = 7
tags = ['javascript', 'coding project']
+++

### Details

Membuat scramble kata menggunakan array, array asli terdapat di baris pertama kode. Silahkan bereksperiment dengan kode tersebut.

### Codes

```js
// Array Original
let secretMessage = ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'JavaScript'];

// Eksperiment dengan kode dibawah
secretMessage.pop();
secretMessage.push('to', 'Program');
secretMessage[secretMessage.indexOf('easily')] = 'right';
secretMessage.shift();
secretMessage.unshift('Programming');
secretMessage.splice(secretMessage.indexOf('get'), 5, 'know');

console.log(secretMessage.length);
console.log(secretMessage.join(' '));
```
Output
```plain
Programming is not about what you know it is about what you can figure out. -2015, Chris Pine, Learn to Program
```
Kamu bisa comment/uncomment atau modifikasi kode tersebut tanpa mengubah array original di *line* `1`.