+++
title = "React Eps III"
draft = false
weight = 4
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""
+++

## Props

Bagaimana kita mengakses properti yang ada di dalam komponen.

```jsx
function App() {
  function clicked() {
    return alert("Button Smashed")
  }

  const username = "Fadhil Suheri"

  return (
    <>
      <Header name={username}/>
      <Button onclick={clicked}/>
    </>
  );
}
```
Disini, kita akan assign properti baru yaitu `name` di komponen `<Header/>`, dengan value `username`.

Bagaimana cara mengaksesnya?

Didalam fungsi komponen `<Button/>` ada sebuah object yang bisa kamu akses dengan membuat parameter (terserah apa namanya), object inilah yang disebut dengan `props` atau properti yang menyimpan semua info tentang komponen  yang sedang digunakan.

```jsx
function Header(props) {
  return (
    <>
      <h1>This is Header: {props.username}</h1>
    </>
  )
}
```

{{< img name=fig1 size=tiny lazy=true >}}

## Mengakses/memanggil sebuah fungsi

Kita punya sebuah fungsi yang akan memanggil dialog alert.

```jsx
function App() {
  function clicked() {
    return alert("Button Smashed")
  }

  return (
    <>
      <Button onclick={clicked}/>
    </>
  );
}
```

Di komponen `Button.js` kamu cukup memanggil fungsi tersebut sama seperti sebelumnya, tapi tanpa `()`.

```jsx
function Button(props) {
  return (
    <>
      <button onClick={props.onclick}>Click Me!</button>
    </>
  )
};
```

Atau kamu bisa juga menggunakan cara yang sama seperti `addEventListener` di vanilla JS.

```jsx
function Button(props) {
  const trigger = () => props.onclick()
  return (
    <>
      <button onClick={trigger}>Click Me!</button>
    </>
  )
};
```

Fungsi `trigger` ini juga menyimpan sebuah `event` didalamnya sama seperti `addEventListener` normalnya.

```jsx
const trigger = (event) => {console.log(event); return props.onclick()}
```