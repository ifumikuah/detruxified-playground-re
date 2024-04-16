+++
title = "React Eps X"
draft = false
weight = 10
tags = ['javascript', 'react']
+++

## Render list

Cara render list di react sangat mudah ketik kita mengandalkan array. Tapi pertama kita membuat sebuah array terlebih dahulu.

```js
const fruits = 
  [{
    name: "Avocado",
    value: 240
  },
  {
    name: "Banana",
    value: 105
  },
  {
    name: "Apple",
    value: 95
  }];
```

Lalu kita akan membuat sebuah komponen `List.js`

```jsx
function List(prop) {
  prop.items.sort((a, b) => a.name.localeCompare(b.name));

  const listItems = prop.items.map((item, i) => <li key={i+1}>{item.name}:&nbsp;{item.value}</li>)
  return (<>
            <h2>{prop.category}</h2>
            <ul>{listItems}</ul>
          </>)
};

export default List;
```

### Penjelasan

1. Kita akan mengakses array melalui prop seperti biasa.

```jsx
// App.js
...
  <List items={fruits} category="Fruits"/>
...
```
Basic untuk mengakses `fruit` yang ada di `App.js` tadi:
```jsx
// List.js
function List(prop) {
  ...
  const listItems = prop.items.map((item, i) => <li key={i+1}>{item.name}</li>)
  ...
};
```
Untuk merender list, diwajibkan agar setiap item memiliki *identifier* unik, disini kita memberi indeks item + 1 sebagai `key`.

2. Lalu render list tersebut

```jsx
// List.js
function List(prop) {
  ...
  const listItems = prop.items.map((item, i) => <li key={i+1}>{item.name}</li>)
  return <ul>{listItems}</ul>
};
```
Diatas adalah basic untuk menampilkan list dari sebuah array.

3. Konfigurasi tambahan terhadap array, sebelum menampilkan array, kamu tentu bisa mem-filter atau sortir array tersebut sedemikian rupa.

```jsx
function List(prop) {
  prop.items.sort((a, b) => a.name.localeCompare(b.name));

  const listItems = prop.items.map((item, i) => <li key={i+1}>{item.name}</li>)
  return <ul>{listItems}</ul>
};
```
Diatas akan menyortir nama list sesuai dengan urutan alfabet (Ascending)

### Additional

Filter list agar hanya menampilkan buah yang sesuai dengan kriteria.

Misal, kriterianya adalah hanya menampilkan buah dengan nilai diatas 100 `fruit.value > 100`.

```jsx
function List(prop) {
  prop.items.sort((a, b) => a.name.localeCompare(b.name));
  const filterItems = prop.items.filter(i => i.value > 100)

  const listItems = filterItems.map((item, i) => <li key={i+1}>{item.name}: {item.value}</li>)
  return <ul>{listItems}</ul>
};
```

### Safety Measure

Kita akan membuat "langkah keamanan" seandainya array tidak ada isinya.

```jsx
function List(prop) {
  const listItems = prop.items.map((item, i) => <li key={i+1}>{item.name}:&nbsp;{item.value}</li>)
  if (prop.items.length > 0) {
    return (<>
              <h2>{prop.category}</h2>
              <ul>{listItems}</ul>
            </>)
  }
  return null;
};
```
Diatas akan mengembalikan `null` atau tidak ada isinya jika array yang diberikan kosong.

Kita juga memberikan nilai default untuk `props` yang ada:

```jsx
List.defaultProps = {
  items: [],
  category: "Category"
}
```
Nilai default `items` adalah array kosong, jadi kalau `items` tidak diisi atau kosong maka komponen ini tidak akan muncul.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-10