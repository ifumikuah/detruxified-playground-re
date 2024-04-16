+++
title = "Javascript 03: Switch case"
draft = false
weight = 9
tags = ['javascript']
+++


### Sinopsis

```js
let groceryItem = 'papaya';

switch (groceryItem) {
    case 'tomato':
        console.log('Tomatoes are $0.49');
        break;
    default:
        console.log('Invalid item');
        break;
}
```

### Details

Merupakan alternatif/variasi dari else if.
```js
let athleteFinalPosition = 'second place';

switch (athleteFinalPosition) {
  case 'first place':
    console.log('You get the gold medal!');
    break;
  case 'second place':
    console.log('You get the silver medal!');
    break;
  case 'third place':
    console.log('You get the bronze medal!');
    break;
  default:
    console.log('No medal awarded.');
    break;
}
```
Output
```plain
You get the silver medal!
```

`dafault` mirip seperti `else`, Output akan mengeksekusi variabel jika tidak ada hasil yang tepat.
