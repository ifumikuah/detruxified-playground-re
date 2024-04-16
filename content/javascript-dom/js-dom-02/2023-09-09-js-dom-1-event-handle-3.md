+++
title = "Event Handle: Event Properties"
draft = false
weight = 3
tags = ['javascript','html']
+++

## Event Properties

Event type yang dipass sebagai argument `.addEventListener` adalah sebuah objek yang menyimpan info tentang event yang berkaitan.

```js
const getBtn = document.getElementById('clickme');

const getEventProp = (event) => {
    console.log(event);
}

getBtn.addEventListener('click',getEventProp);
```
Diatas akan log semua info tentang aktifitas `click` yang ada di `getBtn.addEventListener('click',getEventProp);`.

## Guide

```js
const getBtn = document.getElementById('clickme');

const getEventProp = (event) => {
    console.log(event.target);
}

getBtn.addEventListener('click',getEventProp);
```
Diatas akan log tombol target dari `getBtn` dalam HTML.