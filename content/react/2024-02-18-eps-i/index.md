+++
title = "React Eps I"
draft = false
weight = 2
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "fig2.png"
title = ""
+++

## Bersih-bersih

Karena kita hanya belajar basic, untuk saat ini beberapa file yang ada di `src` bawaan harus dihapus. File yang dihapus ini tidak akan mengganggu berjalannya react, hanya saja saat ini kita tidak membutuhkan file-file tersebut.

{{< hint type=warning >}}
**Hapus semua file KECUALI!!**\
Hapus semua file didalam `src` <u>KECUALI</u>: `App.css`, `App.js`, `index.css`, dan `index.js`
{{< /hint >}}

{{< hint type=important >}}
**Erorr Fix**\
Normalnya, kamu akan mengalami error setelah menghapus file tersebut. Untuk mengatasinya, <u>HAPUS</u> dua buah *line* ini di dalam `App.js`:
```js
// line 1
import logo from './logo.svg';
// line 8
<img src={logo} className="App-logo" alt="logo" />
```

Didalam `index.js`, <u>HAPUS</u> dua buah *line* ini:
```js
// line 5
import reportWebVitals from './reportWebVitals';
// line 17
reportWebVitals();
```

Pesan Error akan hilang setelahnya.
{{< /hint >}}

### Pembersihan lebih lanjut

Kita akan lebih banyak bekerja didalam `App.js`, Hapus element HTML bawaan menyisakan sebuah element pembungkus:

```jsx
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}
```
Menjadi: 
```jsx
function App() {
  return (
    <div>

    </div>
  );
}
```

## Membuat komponen

Hal yang sangat dipuja-puja sama pengguna React.js adalah modularitas dan komponen-able dalam membuat sebuah tampilan UI, maksudnya disini, perintilan UI dibuat modular dan ada tempatnya sendiri-sendiri.

Contohnya, komponen Navbar akan terpisah dengan komponen Modal box, begitu juga komponen lainnya, ini memudahkan maintenance dan fleksibilitas development dalam sebuah tim.

Untuk membuat komponen, kita akan membuat sebuah folder baru didalam `src`, namanya `components`. Lalu didalamnya buat sebuah komponen terserah apa namanya untuk coba-coba.

{{< img name=fig1 size=tiny lazy=true >}}

Karena `App.js` yang kita kerjakan saat ini adalah komponent juga sebenarnya, kita bisa copas apa yang ada didalam `App.js` ke dalam `first.js` lalu modifikasi sedikit kodenya.

```jsx
// import './App.css';
// Kita tidak butuh lagi import './App.css' karena sudah ada di App.js
function First() {
  return (
    <div>
      <h2>Ini komponen First</h2>
    </div>
  );
}

export default First;
```

## Memanggil dan menggunakan komponen

Panggil `first.js` tadi didalam `App.js` dengan cara mengimport ES6.

```jsx
import './App.css';
import First from './components/first';  // Import dengan ES6

function App() {
  return (
    <div>
      <First/> // Letak komponen
      <First/> // Komponen Re-usable
    </div>
  );
}

export default App;
```

## Properti di setiap komponen

Komponen yang sama bisa dikasi properti yang berbeda

```jsx
<div>
  <First hewan="ikan"/>
  <First hewan="kuda"/>
</div>
```

Bagaimana cara mengaksesnya di komponen? Sebuah komponen akan memiliki properti didalamnya, berikan fungsi komponen tersebut sebuah parameter bebas namanya, lalu `console.log` parameter tersebut.

Lihat di console browsermu, komponen yang dirender akan menampilkan properti dalam sebuah `object`:

```jsx
function First(prop) {
  console.log(prop);
  return (
    <div>
      <h2>Nama binatang: </h2>
    </div>
  );
}
```

Lalu kamu bisa mereferensi value tersebut dengan bracket `{}`:
```jsx
function First(prop) {
  console.log(prop);
  return (
    <div>
      <h2>Nama binatang: {prop.hewan}</h2>
    </div>
  );
}
```

{{< img name=fig2 size=tiny lazy=true >}}

Source Github: https://github.com/ifumikuah/learn-react/tree/eps-1