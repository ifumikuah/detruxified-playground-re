+++
title = "Intro: Demo Console"
draft = false
weight = 3
tags = ['javascript','html']
+++

## Document

Untuk manipulasi website dengan DOM, diperlukan akses ke objek `document`. Dibawah adalah contoh memanipulasi HTML dengan console di browser.

![Change Body](/javascript-dom/js-dom-01/2023-09-08-js-dom-1-intro-3/body.gif)

Dengan mengakses `Document`, semua element yang ada di konten dapat dimanipulasi dari `<head>`,`<body>`,`<footer>`, dsb.

![Change Head](/javascript-dom/js-dom-01/2023-09-08-js-dom-1-intro-3/head.gif)

## Embed JS

Untuk mempermudah, ada baiknya embed script di `script.js` daripada menggunakan console. Di `index.html`, gunakan `<script>`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untitled Page</title>
</head>
<body>
    <!-- Contents belong here -->
</body>
<script src="./script.js"></script>
</html>
```