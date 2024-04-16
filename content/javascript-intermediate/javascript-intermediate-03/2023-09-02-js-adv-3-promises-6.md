+++
title = "Javascript Intermediate 03: Promise all"
draft = false
weight = 6
tags = ['javascript']
+++

`Promise.all()` adalah sebuah method untuk memproses banyak promises secara bersamaan, hasilnya akan *rejected* jika salah satu dari sekian banyak promises menghasilkan *rejection*

```js
const memberVote = (leader, empire) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (vote()) {
                console.log(`${leader} from ${empire} voted YES`)
                resolve(empire);
            } else {
                reject(`${leader} from ${empire} voted NO`);
            }
        }, generateRandomDelay());
    });
};


function generateRandomDelay() {
    return Math.floor(Math.random() * 2000);
}

function vote() {
    return (Math.random() > .5);
}

const onFulfill = (passed) => {
  console.log(`Empires voted: ${passed}`);
  console.log(`All leaders pass the vote`);
};

const onReject = (rejectionReason) => {
	console.log(rejectionReason)
};

// Write your code below:
const a = memberVote("Caesar Romulus","Nivendaria");
const b = memberVote("Kai Chi","Technocracy of Mandele");
const c = memberVote("Abbr Babr","Legions of Velandria");
const d = memberVote("Matrix","The Silicons");


Promise.all([a,b,c,d])
  .then(onFulfill)
  .catch(onReject)

```

## Limitations

Method ini kurang efektif dan sangat tidak tertentu.