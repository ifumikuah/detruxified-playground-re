+++
title = "Javascript 09 Project: Meal Maker"
draft = false
weight = 11
tags = ['javascript','project']
+++

Membuat Menu dengan object JavaScript.

```js
const menu = {
    _meal: "",
    _price: 0,
    set meal(mealToCheck){
        if (typeof mealToCheck === 'string') {
            this._meal = mealToCheck;
        }
    },
    set price(priceToCheck){
        if (typeof priceToCheck === 'number') {
            this._price = priceToCheck;
        }
    },
    get todaysSpecial(){
        if ((this._meal) && (this._price)) {
            return `Today's Special is ${this._meal} for $${this._price}!`
        } else {
            return "Error!"
        }
    }
}

menu.meal = "Grimace Shake";
menu.price = 74;

console.log(menu.todaysSpecial);
```