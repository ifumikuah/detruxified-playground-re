+++
title = "Javascript 04 Project: Kertas, Batu dan Gunting"
draft = false
weight = 7
tags = ['javascript', 'coding project']
+++

### Source

```js
const getUserChoice = userInput => {
    userInput = userInput.toLowerCase();

    if (userInput === "rock" || userInput === "paper" || userInput === "scissors" || userInput === "ak47") {
        return userInput;
    } else {
        return "Invalid Input";
    }
};

const getComputerChoice = () => {
    randomNumber = Math.floor(Math.random() * 3);
    switch (randomNumber) {
        case 0:
            return "rock";
            break;
        case 1:
            return "paper";
            break;
        case 2:
            return "scissor";
            break;
        default:
            return "AI is Surrender";
            break;
    }
};

const determineWinner =  (userChoice, computerChoice) => {
    if (userChoice === computerChoice) {
        return "Tied";
    }

    if (userChoice === "rock") {
        if (computerChoice === "paper") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }

    if (userChoice === "paper") {
        if (computerChoice === "scissors") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }

    if (userChoice === "scissors") {
        if (computerChoice === "rock") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }

    if (userChoice === "ak47") {
        return "You Win";
    }
};

const playGame = () => {
    const userChoice = getUserChoice("rock");
    const computerChoice = getComputerChoice();
    if (userChoice === "ak47") {
        console.log(`you just shoot your opponent`);
    } else {
        console.log(`computer throw ${computerChoice}`);
        console.log(`user throw ${userChoice}`);
    }
    
    console.log(determineWinner(userChoice, computerChoice));
};

playGame();
```

### Details

```js
const getUserChoice = userInput => {        
    userInput = userInput.toLowerCase();    // #1

    if (userInput === "rock" || userInput === "paper" || userInput === "scissors" || userInput === "ak47") {  // #2 
    } else {                        // #2
        return userInput;           // #2
        return "Invalid Input";     // #2
    }                               // #2
};
```
 - 1. Mengambil input dari user, huruf input dari user akan di*lowercase* dengan `toLowerCase()`.
 - 2. Mengecek apakah user menginput `"rock"`, `"paper"`, `"scissors"`, `"ak47"`.

```js
const getComputerChoice = () => {
    randomNumber = Math.floor(Math.random() * 3);   // #3
    switch (randomNumber) {
        case 0:                         // #4
            return "rock";
            break;
        case 1:                         // #4
            return "paper";
            break;
        case 2:                         // #4
            return "scissor";
            break;
        default:                        // #4
            return "AI is Surrender";
            break;
    }
};
```
 - 3. *Generate* nomor 0 - 2 untuk komputer.
 - 4. Switch case sesuai dengan nomor yang dikeluarkan oleh `randomNumber`

 ```js
 const determineWinner =  (userChoice, computerChoice) => {
    if (userChoice === computerChoice) {
        return "Tied";
    }

    if (userChoice === "rock") {
        if (computerChoice === "paper") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }

    if (userChoice === "paper") {
        if (computerChoice === "scissors") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }

    if (userChoice === "scissors") {
        if (computerChoice === "rock") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }

    if (userChoice === "ak47") {
        return "You Win";
    }
};
 ```
Mencari pemenang berdasarkan keputusan user vs. computer.
```js
if (userChoice === computerChoice) {
        return "Tied";
    }
```
Jika pilihan user sama dengan computer, maka hasil akan seri.

```js
if (userChoice === "rock") {
        if (computerChoice === "paper") {
            return "Computer Win!";
        } else {
            return "You Win";
        }
    }
```
Jika user memilih `"rock"` tapi computer memilih `"paper"` maka computer menang dan seterusnya untuk pilihan user `"scissors"` dan `"paper`.

```js
if (userChoice === "ak47") {
        return "You Win";
    }
```
Sebuah *cheat* untuk game ini, jika user memilih ak47 maka otomatis menang.

```js
const playGame = () => {
    const userChoice = getUserChoice("rock");
    const computerChoice = getComputerChoice();
    if (userChoice === "ak47") {
        console.log(`you just shoot your opponent`);
    } else {
        console.log(`computer throw ${computerChoice}`);
        console.log(`user throw ${userChoice}`);
    }
    
    console.log(determineWinner(userChoice, computerChoice));
};
```
Mendeklarasikan fungsi untuk bermain game, dengan memanggil fungsi-fungsi diatas tadi.

```js
playGame();
```
Untuk memanggil `playGame()` dan memulai permainan.

# Questions ?

## "userInput = userInput.toLowerCase();" ?

Seandainya user memasukkan `"Rock"` atau `"ROCK"`, maka akan diubah menjadi `"rock"` untuk mengatasi perbedaan kapitalisasi huruf

## kenapa getComputerChoice() tidak memiliki parameter ?

Karena kita tidak memerlukan input lagi untuk komputer, komputer hanya bertugas mengeluarkan `rock`, `scissors`, `paper` secara acak.

## kenapa playGame() tidak memiliki parameter ?

`playGame()` bertugas untuk menyatukan/menyusun ketiga fungsi diatas tadi. Sedangkan kita hanya perlu input dari `getUserChoice(userInput)` untuk memulai permainan.