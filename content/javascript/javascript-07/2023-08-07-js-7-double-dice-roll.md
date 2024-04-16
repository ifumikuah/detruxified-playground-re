+++
title = "Javascript 07: Double Dice Roll"
draft = false
weight = 1
tags = ['javascript','coding Project']
+++

### Details

Membuat roll dua dadu secara acak dengan while loop, jika kedua dadu menghasilkan 6, maka loop akan berhenti.

### Code

```js
diceNumbers = [1,2,3,4,5,6];

let firstDice;
let secondDice;
while ((firstDice !== 6) || (secondDice !== 6)) {
    firstDice = diceNumbers[Math.floor(Math.random() * diceNumbers.length)];
    secondDice = diceNumbers[Math.floor(Math.random() * diceNumbers.length)];

    if ((firstDice === 6) && (secondDice === 6)) {
        console.log('You hits 6 on both dice');
    } else {
        console.log(`${firstDice} ${secondDice}`);
    }
};
```
Kode diatas akan membuat roll dadu berdasarkan index `diceNumbers`. 

Jika kondisi `((firstDice !== 6) || (secondDice !== 6))` memiliki nilai `false` maka artinya kedua dadu menghasilkan jumlah 12/(6,6).

### Bagaimana ((firstDice !== 6) || (secondDice !== 6)) menjadi false ?

Jika kamu memutar satu dadu, kondisi `false` akan terpenuhi jika `6 != 6`.

Dengan menggunakan logika OR di antara dua dadu, kamu bisa membuat pengulangan berhenti hanya disaat dadu pertama dan dadu kedua menghasilkan total angka 12.

*12 hanya bisa dicapai jika putaran kedua dadu menghasilkan 6 disaat yang sama.*

### Tabel Kebenaran OR

| Ia| Ib |  O    |
| --|--  | ---   |
| 0 | 0  |   0   |
| 1 | 0  |   1   |
| 0 | 1  |   1   |
| 1 | 1  |   1   |

> Ingat di poin pertama!, jika kamu memutar sebuah dadu, maka dadu akan berhenti disaat angka 6 keluar, ini artinya momentum disaat `firstDice = 6` yang mana kondisi tersebut sudah menjadi `false` ((`6 != 6`) = `false`)

