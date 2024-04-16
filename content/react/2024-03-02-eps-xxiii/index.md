+++
title = "React Eps XXIII"
draft = false
weight = 23
tags = ['javascript', 'react']
+++

## useRef

Hooks `useRef()` berfungsi untuk menyimpan sebuah value / nilai yang tidak ada kaitannya dengan rendering. Value yang ada didalam `useRef` ini mutable (mirip `let`) dan juga tidak ada pengaruh render jika nilainya berubah.

```jsx

import React, { useRef } from 'react'

export default function App () {
  const reference = useRef(0)
}
```

Nilai `0` atau nilai default yang ada di dalam `useRef` tersebut disimpan didalam sebuah object, jika kamu log isinya akan seperti ini:

```jsx
...
  console.log(reference)
...
```
```plain
 {current: 0}
```

Dia cuma menyimpan sebuah object dengan isi sebuah key, yaitu `current`.

### Menghitung berapa kali tombol di tekan

Setiap kali sebuah tombol ditekan, sebuah fungsi untuk merender sesuatu akan dieksekusi. `useRef` bisa digunakan untuk menghitung berapa kali tombol sudah ditekan karena hooks ini sendiri mengabaikan render.

```jsx
export default function UseRef() {
  const [counter, setCounter] = useState(0);
  const occurence = useRef(0)

  const tallyCounter = () => { 
    occurence.current ++ // Menambah 1 setiap tombol ditekan
    setCounter(c => c + 1)
  }

  return (
    <>
      <h2>Counter: {counter}</h2>
      <button onClick={tallyCounter}> Count </button>
      <p> Button clicked {occurence.current} times </p>
    </>
  )
}
```
`occurence.current ++` Akan menghitung setiap `tallyCounter()` dijalankan (setiap tombol ditekan).

### Mengakses element DOM

`useRef` juga bisa mengakses elemen didalam DOM. atribut `ref` digunakan pada elemen jika mau mengakses elemen tersebut

```jsx
function App() {
  const inputElement = useRef();

  const focusInput = () => {
    inputElement.current.focus();
  };

  return (
    <>
      <input type="text" ref={inputElement} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}
```
Contoh sederhana, diatas akan membuat form input dalam mode focus tanpa kita mengklik form tersebut (melalui tombol sesudahnya)

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-23