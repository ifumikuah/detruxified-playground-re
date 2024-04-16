+++
title = "React Eps VI"
draft = false
weight = 6
tags = ['javascript', 'react']
+++

## Styling di React

Ada 3 cara styling di react:

1. Global CSS Styling
2. Module CSS Styling
3. Inline Styling

### Global Styling

Styling sama seperti HTML CSS vanilla, styling komponen diletakkan pada satu file `style.css`.

Pertama, kamu cukup import `style.css` kamu di `App.js` atau `index.js`

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './reset.css'; // Import reset.css
import './index.css'; // Import index.css untuk global styling
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

Lalu untuk menggunakan mengaplikasikan class `title` yang ada di `index.css`:

```jsx
function App() {
  return (
    <>
      <h1 className="title">Title</h1>
      <Card/>
      <Card/>
      <Button/>
    </>
  );
}
```

### Module Styling

Styling modular, styling ini bersifat lokal. Jadi misalkan ada dua nama class yang sama di global dan local atau sebaliknya, tidak akan menjadi masalah.

Cara terbaik untuk membuat styling modular seperti ini adalah dengan membuat komponen beserta stylingnya berada dalam satu direktori.

```plain
|- Components
|   |
|   |- Card
|       |
|       |- Card.js
|       |
|       |- Card.module.css
|
|- App.js
|
|- index.js
|
|- index.css
``` 

Didalam `Card.js`, buat sebuah CSS tambahkan `.module` sebelum ekstensi CSS nya, menandakan kalau itu module. Lalu import sabagai `card` dari `'./Card.module.css'`. Import tersebut disimpan sebagai object `card`, dan mengaksesnya mirip seperti object.

```jsx
// Card.js
import profilepic from '../assets/profile.jpg';
import card from './Card.module.css';

function Card() {
  return (
    <div className={card.card}>
      <img className={card.cardImg} src={profilepic} alt='profile' width="150" height="150"/>
      <h3>John Doe</h3>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
    </div>
  )
};

export default Card;
```
```css
/* Card.module.css */
.card {
  width: 350px;
  height: 250px;
  padding: .5rem;
  margin: 1rem;
  text-align: center;
  display: inline-block;
  border: 2px solid gray;
  border-radius: .5rem;
}

.cardImg {
  border-radius: 75px;
}
```

### Inline Styling

Inline styling adalah styling dalam bentuk object berada dalam satu komponen yang sama.

```jsx
// Button.js
function Button() {
  const styles = {
    padding: ".6rem 1rem",
    backgroundColor: "#3d9956",
    color: "#fff",
    fontSize: "2rem",
    borderRadius: ".5rem",
    border: "none",
    cursor: "pointer"
  }
  
  return (
    <>
      <button style={styles}>button</button>
    </>
  )
};
```

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-6