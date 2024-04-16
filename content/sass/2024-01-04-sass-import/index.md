+++
title = "Sass 12: Import dan Partial"
draft = false
weight = 12
tags = ['css', 'sass']
+++

Menggunakan partial untuk mengimport komponen scss terpisah.

```plain
|
|- index.html
|
|- partials/
|  |
|  |- _mixins.scss
|  |
|  |- _variables.scss
|  |
|  |- _placeholders.scss
|
|- main.scss

```

Partial ditandai dengan file berawalan `_`, sass akan mengidentifikasi file tersebut sebagai partial.

Untuk mengimport, lakukan hal yang sama dengan CSS:

```scss
// main.scss
@import "helper/placeholders";
@import "helper/variables";
@import "helper/mixins";
```

