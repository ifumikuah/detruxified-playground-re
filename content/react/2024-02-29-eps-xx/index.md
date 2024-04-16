+++
title = "React Eps XX"
draft = false
weight = 20
tags = ['javascript', 'react']
+++

## useEffect

Hook `useEffect` simplenya adalah "side function", maksud "side function" ini adalah `useEffect` akan dieksekusi jika "X" terjadi.

Ada berapa "X" itu?

### Setiap render

Ingat react akan re-render setiap ada perubahan, bentuk `useEffect` pertama adalah akan mengeksekusi `code` didalamnya di setiap render dilakukan.

```jsx
useEffect(() => {
  // code
})
```

Contoh, membuat jam yang secara live menghitung detiknya:

```jsx
export default function Clock () {
  const [clock, setClock] = useState(new Date().toLocaleTimeString("en-ID"));

  useEffect(() => {
    setTimeout(() => {
      setClock(new Date().toLocaleTimeString("en-ID"))
    }, 1000)
  })

  return (
    <>
      <h2>{clock}</h2>
    </>
  );
}
```

### Saat render pertama

`useEffect` ini hanya berjalan saat render pertama.

```jsx
useEffect(() => {
  // code
}, [])
```

Diatas adalah bentuk default dari `useEffect`, `useEffect` menerima dua argument yaitu:

- Sebuah callback untuk eksekusi.
- Array, array yang ada di hook ini (`useEffect`) disebut juga dengan istilah *dependency*. 

Jika dependency kosong, maka `useEffect` akan dijalankan hanya sekali, yaitu pada saat render pertama (saat halaman loaded)

Contoh, tracking koordinat kursor:

```jsx
export default function Cursor() {
  const [coords, setCoords] = useState({x: 0, y:0});

  useEffect(() => {
    function getCoords(event) {
      setCoords(c => c = {x: Math.round(event.clientX), y: Math.round(event.clientY)})
    }
    window.addEventListener("pointermove", getCoords)
  }, []);

  return (
    <>
      <h2>X Coords: {coords.x}</h2>
      <h2>Y Coords: {coords.y}</h2>
    </>
  );
}
```

Kita hanya menjalankan `window.addEventListener()` sekali saat render pertama. Jika kita menjalankan code dengan tujuan yang sama tapi tanpa `useEffect`, seperti ini: 

```jsx
export default function Cursor() {
  const [coords, setCoords] = useState({x: 0, y:0});

  window.addEventListener("pointermove", (event) => {
    setCoords(c => c = {x: Math.round(event.clientX), y: Math.round(event.clientY)})
  })

  return (
    <>
      <h2>X Coords: {coords.x}</h2>
      <h2>Y Coords: {coords.y}</h2>
    </>
  );
}
```

Diatas juga tetap bekerja sama halnya seperti sebelumya, tetapi perbedaan krusial ada didalam isu performa. Dimana kode pertama hanya dieksekusi sekali saat render pertama saja.

Sedangakan di kode kedua, event listener tersebut akan dijalankan setiap kali rendering dilakukan, dimana event listener tersebut akan menumpuk sehingga muncul isu performa yang tidak diinginkan.

Terlebih lagi `useEffect` ini akan menjalankan sebuah *cleanup* jika kamu mereturn sebuah callback didalamnya. Cleanup ini digunakan untuk pembersihan jejak (trace) dari siklus eksekusi `useEffect` sebelumya.

```jsx
export default function Cursor() {
  ...
  useEffect(() => {
    function getCoords(event) {
      setCoords(c => c = {x: Math.round(event.clientX), y: Math.round(event.clientY)})
    }
    window.addEventListener("pointermove", getCoords)
    return () => {
      window.removeEventListener("pointermove", getCoords)
    }
  }, []);
  ...
}
```

### Saat render pertama & update dependencies

Dependencies diisi dengan value yang memiliki reaksi disaat rendering, disini salah satunya value atau getter yang ada di `useState`.

Mengupdate judul window menjadi koordinat kursor saat ini:

```jsx
export default function Cursor() {
  const [coords, setCoords] = useState({x: 0, y:0});

  useEffect(() => {
    function getCoords(event) {
      setCoords(c => c = {x: Math.round(event.clientX), y: Math.round(event.clientY)})
    }
    window.addEventListener("pointermove", getCoords)
  }, []);

  useEffect(() => {
    document.title = `${coords.x} ${coords.y}` // Update judul window
  }, [coords])

  return (
    <>
      <h2>X Coords: {coords.x}</h2>
      <h2>Y Coords: {coords.y}</h2>
    </>
  );
}
```

```jsx
  useEffect(() => {
    document.title = `${coords.x} ${coords.y}` // Update judul window
  }, [coords])
```

`useEffect` tersebut akan mengawasi pergerakan dari `coords` dan akan mentrigger code didalamnya jika ada perubahan terhadap dependency tersebut.


Github Source: https://github.com/ifumikuah/learn-react/tree/eps-20