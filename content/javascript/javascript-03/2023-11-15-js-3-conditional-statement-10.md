+++
title = "Javascript 07: Break and Continue"
draft = false
weight = 12
tags = ['javascript']
+++

`break` dan `continue` adalah dua statement untuk mengendalikan control flow. Dua statement ini paling sering digunakan dalam `switch` case dan looping

## Break

Menghentikan eksekusi yang ada didalam bloknya.

```js
const arr = range(1,60,3) // fungsi yang generate hasil perkalian 3 [3...60]
let newArr = []; // for output

for (index in arr) {
    // Sebuah if untuk mencari apakah element didalam array adalah genap (dapat dibagi 2)
    if (arr[index] % 2 === 0) {
        break
    }
    newArr.push(arr[index])
}

console.log(newArr);
// Output: [ 3 ]
```

Seperti contoh diatas, `break` menghentikan perulangan tersebut disaat menemukan angka genap.

## Continue

`continue` meloncati/melewati atau *skip* eksekusi yang ada didalam bloknya.

```js
// Contoh masih sama dengan yang diatas, perbedaan hanya `break` diganti menjadi `continue`
...
    if (arr[index] % 2 === 0) {
        continue
    }
...

console.log(newArr)
// Output: [3, 9, 15, 21, 27, 33, 39, 45, 51, 57]
```

`continue` melompati setiap blok perulangan disaat menemukan angka genap.