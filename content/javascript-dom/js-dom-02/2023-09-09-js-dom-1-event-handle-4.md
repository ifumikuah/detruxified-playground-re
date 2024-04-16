+++
title = "Event Handle: Keyboard Events"
draft = false
weight = 4
tags = ['javascript','html']
+++

Sama seperti event pada umumnya, Key event akan handle event ketika user menekan tombol di keyboard.

```js
const getForm = document.getElementById('form');

const keyEvent =()=> {
    alert("You pressed a key inside the input field");
}

getForm.addEventListener('keypress',keyEvent);
```

Diatas akan menampilkan dialog peringatan jika menekan sesuatu di form `getForm`.