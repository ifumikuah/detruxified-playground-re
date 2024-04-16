+++
title = "Javascript 03: else"
draft = false
weight = 2
tags = ['javascript']
+++


### Synopsis

```js
if (false) {
  console.log('The code in this block will not run.');
} else {
  console.log('But the code in this block will!');
}
```

### Details

Mengeksekusi blok *else*, jika syarat tidak memenuhi blok if

```js
let sale = true;

sale = false;

if(sale) {
  console.log('Time to buy!');
} else {
  console.log('Time to wait for a sale.');
}

```

Output

```plain
Time to wait for a sale.
```