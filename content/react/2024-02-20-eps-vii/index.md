+++
title = "React Eps VII"
draft = false
weight = 7
tags = ['javascript', 'react']
+++

## PropTypes

`PropTypes` berguna untuk validasi tipe data yang dimiliki oleh `props`.

Pertama, import dulu sebagai `PropTypes` dari `'prop-types'`:

```jsx
import PropTypes from 'prop-types'
```

Lalu kita akan setel datatypes tertentu di setiap `props`:

```jsx
function Card(prop) {
  return (
    <div className={card.card}>
      <img className={card.cardImg} src={profilepic} alt='profile' width="150" height="150"/>
      <h3 className={card.cardTitle}>{prop.name} ({prop.age})</h3>
      <p className={card.cardDesc}>{prop.hobby}</p>
    </div>
  )
};

Card.propTypes = {
  name: PropTypes.string, // Membuat name agar hanya menerima datatype: string
  hobby: PropTypes.string, // Membuat hobby agar hanya menerima datatype: string
  age: PropTypes.number // Membuat age agar hanya menerima datatype: number
}
```

Lalu kita akan mencubanya di `App.js`:

```jsx
...
  <Card name={"Fadhil"} hobby={"Mancing"} age={34}/>
  <Card name={"Deni"} hobby={"Membaca"} age={"26"}/>
...
```

Jika datatypes tidak sesuai, seperti contohnya disini `age={"26"}`, maka hanya mengeluarkan peringatan kesalahan:

```plain
App.js:9 Warning: Failed prop type: Invalid prop `age` of type `string` supplied to `Card`, expected `number`.
  at Card
```

Namun, ini sangat berguna untuk debugging di tingkat lanjut.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-7