+++
title = "React Eps IV"
draft = false
weight = 5
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""
+++

## State

State adalah keadaan pada element di React, *hooks* `useState` mengatur keadaan state di React.

Untuk membuat `useState`, kamu perlu mengimpor `useState` dulu.

```jsx
import React, {useState} from 'react';
```

Sekarang kita akan membuat sebuah `useState`. `useState` memerlukan dua buah variable untuk disimpan, yaitu pertama, nilai awal, dan kedua fungsi yang akan digunakan untuk manipulasi.

Kita akan membuat sebuah counter, seperti counter zikir.

```jsx
const [counter, setCounter] = useState(0)
```

`counter` menyimpan nilai awal `0`, sesuai dengan `useState(0)`.

Lalu kita akan membuat sebuah fungsi yang akan mengupdate counter + 1.

```jsx
function updateCounter() {
  setCounter(counter + 1)
}
```

Kode diatas, akan menjalankan fungsi `setCounter` dan hasil `setCounter` akan disimpan menjadi `counter` (mengubah nilai awal dari `counter` menjadi `counter + 1`). 

Sekarang kita perlu sebuah tombol untuk mentrigger fungsi ini.

```jsx
function App() {
  const [counter, setCounter] = useState(0)

  function updateCounter() {
    setCounter(counter + 1)
  }

  return (
    <>
      <h2>You clicked the button {counter} times</h2>
      <Button click={() => updateCounter()}/>
    </>
  );
}
```
`<Button/>` adalah component tersendiri, ini isinya:
```jsx
function Button(props) {
  return (
    <>
      <button onClick={props.click}>Click Me!</button>
    </>
  )
};
```

{{< img name=fig1 size=tiny lazy=true >}}

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-4