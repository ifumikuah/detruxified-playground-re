+++
title = "Javascript Intermediate 04: Error handling"
draft = false
weight = 4
tags = ['javascript']
+++

Jika rejection di Promises biasa di handle oleh `.catch`, maka async dihandle oleh `catch`.

```js
const link = async () => {
    console.log("Linking to server, please wait...");
    try {
        const passed = await connect();
        console.log("Congrats: ",passed);
    } catch (error) {
        console.log(error);
        console.log("Sorry, we can't make it happen");
    }
}
```
`console.log(error)` akan log alasan *Rejection* dari Promises dibawah

```js
const probability = () => Math.random() < .4; // Generate 60% chance of success

const connect = () => {
    return new Promise((resolve, reject) => {
        const time = Math.floor(Math.random()*5000)
        setTimeout(() => {
            if (probability()) {
                const status = "Connected"
                resolve(status)
            } else {
                const status = "Error 404" // Rejection reason
                reject(status)
            }
        }, time);
    })
}
```