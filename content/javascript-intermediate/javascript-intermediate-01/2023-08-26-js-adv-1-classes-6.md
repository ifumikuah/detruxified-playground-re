+++
title = "Javascript Intermediate 01: Inheritance Extended"
draft = false
weight = 6
tags = ['javascript']
+++

Membuat `baldEagle` sub-class dengan fungsi yang complex.

```js
class Bird extends Animal {
    constructor(name,mobility,altitude){
        super(name,mobility);
        this._fly = true;
        this._altitude = altitude;
        this._weather = "Warm";
    }
    get fly(){
        return `Fly status: ${this._fly}`;
    }
    get altitude(){
        return `Altitude: ${this._altitude}`;
    }
    get weather(){
        return `${this._weather}, mobility adjusted to ${this._mobility}`;
    }
    getWeather(){
        const weather = ["Thunderstorms","Rain","Windy","Warm","Hot"];
        const weatherRoll = weather[Math.floor(Math.random() * weather.length)];
        this._weather = weatherRoll;

        switch (weatherRoll) {
            case "Thunderstorms":
                return this._mobility = this._mobility - (this.mobility * 0.64);
                break;
            case "Rain":
                return this._mobility = this._mobility - (this.mobility * 0.32);
                break;
            case "Windy":
                return this._mobility = this._mobility + (this.mobility * 0.16);
                break;
            case "Warm":
                return this._mobility
                break;
            case "Hot":
                return this._mobility = this._mobility - (this.mobility * 0.08);
                break;

        }
    }
}
```

## Weather method

Method `getWeather` akan generate acak nilai cuaca dan akan memberikan penalti terhadap initial `mobility` sebesar:

| Weather | Penalti |
|-|-|
| Thunderstorms | -64% |
| Rain | -32% |
| Windy | +16% (Buff) |
| Warm | +0% (Default) |
| Hot | -8% |

Lalu method getter `weather` akan memberi informasi tentang jenis cuaca beserta `mobility` sesudah penalti.

## Hasil

```js
const baldEagle = new Bird("Tiger Lake",1000,4500);
baldEagle.getWeather();
console.log(baldEagle.name);
console.log(baldEagle.weather);
```
```plain
Tiger Lake
Windy, mobility adjusted to 1160
```