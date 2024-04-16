+++
title = "React Eps XVII"
draft = false
weight = 17
tags = ['javascript', 'react']
+++

## Update Array di useState

Pertama, mari membuat sebuah array:

```jsx
const [fish, setFish] = useState(["Tilapia", "Carp", "Piranha"]);
```

Elemen yang akan dirender:

```jsx
return (
    <>
      <ul>
        {fish.map((x,i) => <li key={i}>{x}</li>)}
      </ul>
      <input type="text" id="addFish"/>
      <button>submit</button>
    </>
  )
```
List ikan tersebut akan dirender dari `Array.prototype.map()`. Ingat setiap item di list harus ada unique `key` nya tersendiri, `index` item akan dijadikan sebagai `key` dicontoh ini.

Tambahkan sebuah id pada input, itu akan dibutuhkan nantinya.

### Menambah ikan

Pertama, kita akan membuat fungsi untuk tambah kedalam item.

```jsx
const addFish = () => {
    const fishToAdd = document.getElementById("addFish").value; // Store the fish before it get erased by line below
    document.getElementById("addFish").value = "";

    setFish(f => [...f, fishToAdd])
  };
```

Gunakan id yang ada di `<input>` tadi untuk menangkap value ikan sementara dan menyimpannya kedalam variable `fishToAdd`. Setelah ikan tersimpan, maka teks yang ada di input terlihat kosong, namun value ikan yang sebelumnya sudah sempat disimpan sama `fishToAdd`.

```jsx
setFish(f => [...f, fishToAdd])
```

Dengan cara yang mirip (spread syntax) object, kita akan menambah ikan tersebut kedalam `fish`.

Tambahkan *trigger* fungsi tersebut di `<button>`:
```jsx
<button onClick={addFish}>submit</button>
```

### Menghapus ikan

Untuk menghapus ikan, kita akan membuat fitur dimana item harus diklik untuk menghapusnya.

```jsx
const delFish = (key) => {
    setFish(
      f => f.filter((_,i) => i !== key)
    )
  }
```

Fungsi `Array.prototype.filter()` diatas akan mereturn item dengan indeks yang sama dengan `key` TAPI kebalikannya, **jadi yang direturn akhirnya semua item KECUALI item dengan indeks yang sama dengan `key`**.

Parameter `key` dibutuhkan untuk argument pas *trigger* nanti.

```jsx
<ul>
  {fish.map((x,i) => <li key={i} onClick={() => delFish(i)}>{x}</li>)}
</ul>
```

Penjelasan triggering pada list untuk menghapus item:

```jsx
onClick={() => delFish(i)}
```

Ketika di klik, maka indeks pada list tersebut akan dijadikan argument untuk parameter `key` sebelumnya tadi.

Ini membuat `key` memiliki value yang sama dengan `i` yang ada di `delFish()` tadi.

```js
f => f.filter((_,i) => i !== key)
// Artinya jika kita mengklik list dengan indeks 2 (list ke 3)
console.log(2 !== 2) // False
```

Ingat, `Array.prototype.filter()` hanya return item yang bernilai `true`/truthy, jadi berdasarkan fungsi diatas, kesimpulannya adalah fungsi `f.filter()` diatas membuat item yang kita klik menjadi `false` untuk dikeluarkan/dihapus.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-17