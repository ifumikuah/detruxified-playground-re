+++
title = "React Eps XI"
draft = false
weight = 11
tags = ['javascript', 'react']
+++

## Click Events

Click events, menjalankan set perintah tertentu yang ada difungsi saat sebuah komponen/element di klik.

Kita akan membuat sebuah *onClick* event paling basic yang pernah ada:

```jsx
// Button.jsx
function Button() {
  const styles = { } // Styling
  const executor = () => {
    console.log("Click!");
  }
  
  return (
    <>
      <button onClick={executor} style={styles}>Touch Me!</button>
    </>
  )
};

export default Button;
```

Untuk membuat sebuah onClick event, kamu membutuhkan callback function. Contoh diatas, ketika `<button>` di klik, maka akan menjalankan sebuah callback function `executor`.

### w/ Parameter

Bagaimana jika sebuah fungsi dengan parameter?

Sama saja, namun kamu membungkus fungsi tersebut didalam sebuah callback lagi didalam event handler `onClick` tersebut.

```jsx
// Button.jsx
function Button() {
  const styles = { } // Styling
  const executor = (str) => {
    console.log(str);
  }
  
  return (
    <>
      <button onClick={() => executor("Greetings")} style={styles}>Touch Me!</button>
    </>
  )
};

export default Button;
```

### Event Object

Ketika kamu mentrigger sebuah event handler (interaksi mengklik, hovering, keypress) sebuah element. Callback yang ada di `onClick` tadi menyimpan informasi tentang event terkait.

Cara mengaksesnya sama seperti `addEventListener` di vanilla JS:

```jsx
function Button() {
  const styles = { } // Styling
  const executor = (event) => {
    console.log(event);
  }
  
  return (
    <>
      <button onClick={(e) => executor(e)} style={styles}>Touch Me!</button>
    </>
  )
};

export default Button;
```

Dibawah adalah contoh untuk mengganti text yang ada dibutton saat diklik:

```jsx
function Button() {
  const styles = { } // Styling
  const executor = (event, str) => {
    event.target.innerText = str;
  }
  
  return (
    <>
      <button onClick={(e) => executor(e, "Woooo!")} style={styles}>Touch Me!</button>
    </>
  )
};

export default Button;
```

Kamu bisa melakukan apa saja seperti mengganti styling, mematikan display element tertentu. Sama halnya seperti manipulasi DOM di vanilla JS.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-11