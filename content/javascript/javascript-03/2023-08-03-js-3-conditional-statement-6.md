+++
title = "Javascript 03: or Shorthand"
draft = false
weight = 6
tags = ['javascript']
+++

### Details

Dengan mengkombinasikan, Truthy or Falsy dan Logical Operators, kita bisa mempersingkat sebuah if else...

```js
let username = '';
let defaultName;
 
if (username) {
  defaultName = username;
} else {
  defaultName = 'Stranger';
}
 
console.log(defaultName);
```

Contoh diatas memiliki output `Stranger` dikarenakan `username` memiliki nilai `false`.

Kita bisa mempersingkat kode diatas dengan sebuah *shorthand* operator `||`

```js
let username = '':

defaultUsername = username || 'Guest';

console.log(defaultUsername);
```

Output adalah `Guest` karena operator `||` hanya meneruskan nilai `true`.
