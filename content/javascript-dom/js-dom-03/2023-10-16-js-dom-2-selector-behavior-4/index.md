+++
title = "Selector Behavior: getElements*"
draft = false
weight = 4
tags = ['javascript']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "fig2.png"
title = ""

[[resources]]
name = "fig3"
src = "fig3.png"
title = ""

[[resources]]
name = "snippet1"
src = "snippet1.png"
title = ""
+++

`getElements*` berlaku untuk:
- `getElementsByClassName()`
- `getElementsByTagName()`
- `getElementsByName()`

Method ini *return* NodeList berbentuk Live HTMLCollection.

## Live NodeList

Berbeda dengan [static NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList#static_nodelists) milik `querySelectorAll()`, [live NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList#live_nodelists) membuat DOM otomatis mengupdate setiap perubahan yang terjadi dalam DOM.

## NodeList Behavior

Untuk memahaminya, kita perlu melihat apa yang terjadi jika kita menambahkan sebuah element melalui DOM.

Scenario, kita mempunyai sebuah unordered list `<ul>`, kemudian kita akan menambah dan mengurangi item didalamnya melalui DOM.

{{< img name=fig1 lazy=true size=medium >}}

### Static NodeList

{{< img name=fig2 lazy=true size=medium >}}

Kode untuk keperluan observasi:

```js
const staticList = document.querySelectorAll('.item')
console.log(`Selected elements saved as staticList`);
console.log(`staticList.length before adding item: ${staticList.length}`);

console.log(`we starting to add item...`);

function addItem() {
    const newItem = document.createElement('li');
    newItem.innerHTML = "This item added by DOM"
    newItem.className = "item"
    document.getElementById('myList').appendChild(newItem)
}
addItem()
addItem()

console.log(`we have added 2 new items with DOM, there should be 5 length of staticList`);
console.log(`staticList.length after adding item: ${staticList.length}`);

console.log(`okay, we need to remove one element from the lists`);
function removeItem() {
    const itemsToRemove = document.getElementById('myList').getElementsByClassName('item');
    itemsToRemove[itemsToRemove.length - 1].remove()
}
removeItem()
console.log(`staticList.length after removing one item: ${staticList.length}`);
```

### Live NodeList

{{< img name=fig3 lazy=true size=medium >}}

Kode:

```js
const liveList = document.getElementsByClassName('item')
console.log(`Selected elements saved as liveList`);
console.log(`liveList.length before adding item: ${liveList.length}`);

console.log(`we starting to add item...`);

function addItem() {
    const newItem = document.createElement('li');
    newItem.innerHTML = "This item added by DOM"
    newItem.className = "item"
    document.getElementById('myList').appendChild(newItem)
}
addItem()
addItem()

console.log(`we have added 2 new items with DOM, there should be 5 length of liveList`);
console.log(`liveList.length after adding item: ${liveList.length}`);

console.log(`okay, we need to remove one element from the lists`);
function removeItem() {
    const itemsToRemove = document.getElementById('myList').getElementsByClassName('item');
    itemsToRemove[itemsToRemove.length - 1].remove()
}
removeItem()
console.log(`liveList.length after removing one item: ${liveList.length}`);
```

## Perbedaan Lainnya

Hasil yang di *return* `getElements*` bukan sebuah array, jadi kamu tidak bisa menggunakan method array seperti ` querySelectorAll()`.