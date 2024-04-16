+++
title = "Javascript 03 Project 2: Race"
draft = false
weight = 11
tags = ['javascript', 'coding project']
+++

# Details

Membuat prioritas partisipan dalam perlombaan lari dengan syarat :

umur 13 - 27

daftar lebih awal akan mendapatkan jam lebih awal yang sudah ditentukan


- class a umur 13 - 15 akan dimulai pada jam 10:00

- class b umur 16 - 18 akan dimulai pada jam 08:30

- class c umur 18 - 21 akan dimulai pada jam 09:30

- class d umur 22 - 27 akan dimulai pada jam 10:30

peserta umur 16 - 21 yang daftar lebih awal akan dimulai pada jam

- class b 08:00
- class c 09:00

nomor : 
- kelas b atau c yang mendaftar lebih awal akan mendapatkan nomor dibawah seratus
- yang lainnya akan mendapatkan nomor diatas 100

# Code

```js
let randNum = Math.floor(Math.random() * 1000);

const earlyReg = false;
const runnerAge = 17;


if (runnerAge > 27 ) {
    console.log("You're too old to participate");
} else if (runnerAge < 13) {
    console.log("You're too young to participate");
} else if (runnerAge <= 15) {
    console.log(`Your race will start at 10:00 AM, #${randNum}`)
} else if (runnerAge <= 18 && earlyReg) {
    randNum = Math.floor(randNum / 10)
    console.log(`Your race will start at 08:00 AM, #${randNum}`)
} else if (runnerAge <= 21 && earlyReg) {
    randNum = Math.floor(randNum / 10)
    console.log(`Your race will start at 09:00 AM, #${randNum}`)
} else if (runnerAge <= 18 && !earlyReg) {
    console.log(`Your race will start at 08:30 AM, #${randNum}`)
} else if (runnerAge <= 21 && !earlyReg) {
    console.log(`Your race will start at 09:30 AM, #${randNum}`)
} else if (runnerAge <= 27) {
    console.log(`Your race will start at 10:30 AM, #${randNum}`)
} else {
    console.log("Invalid Data!");
}
```