+++
title = "React Eps XXII"
draft = false
weight = 22
tags = ['javascript', 'react']
+++

## useContext

Hook ketiga, yaitu `useContext`. Hook ini mempermudah penggunaan state antar component.

## Prop Drilling

Tanpa menggunakan `useContext`, untuk menggunakan state antar component diperlukan `prop`.

```jsx
// ComponentA

export default function ComponentA () {
  const [user, setUser] = useState("Erick")

  return (
    <div>
      <ComponentB user={user}/>
    </div>
  )
}
```
```jsx
export default function ComponentB ({user}) {

  return (
    <div>
      <p>Hi {user}</p>
    </div>
  )
}
```

Diatas mengharuskan `ComponentB` meneruskan sebuah props `user` untuk mengakses nama tersebut. Namun, apa jadinya jika Component tersebut *nested*, pasti kita harus meneruskan props berulang kali disetiap component yang membungkusnya, inilah yang disebut dengan *Prop Drilling*, meneruskan prop di lapisan demi lapisan sampai komponen yang dituju.

## Menggunakan useContext

Ada dua fungsi yang harus kita import untuk mengerjakan ini:

- `createContext` untuk component provider (pemberi) state tersebut
- `useContext` untuk component yang akan menggunakan state tersebut

Misal, kita akan membuat sebuah state `user` untuk username di komponen `ComponentA` dan state tersebut akan digunakan oleh komponen `ComponentB`.

### Component A

Import fungsi `createContext` untuk mempersiapkan state yang akan *didistribusi*:

```jsx
import ComponentB from "./ComponentB";
import React, { useState, createContext } from "react";
```

Untuk *Distribusikan* state tersebut kita harus mengexport context agar tersedia di global.

```jsx
export const UserContext = createContext()
```

Didalam fungsi komponen, pastikan kamu sudah membuat `useState` untuk `user`. Disini, komponen yang akan menggunakan state `user` harus dibungkus dalam sebuah elemen provider dari `UserContext` yang kita buat tadi.

```jsx
export default function ComponentA() {
  ...

  return (
    <div className="container">
      <h2>Component A</h2>
      <UserContext.Provider value={user}>
        <h3>Below is ComponentB</h3>
        <ComponentB />
      </UserContext.Provider>
      ...
    </div>
  );
}
```

### Component B

Untuk komponen A sudah selesai, tinggal membuat komponen B agar bisa menerima state `user` yang ada di komponen A.

Import `useContext` dari react:

```jsx
import React, { useContext } from "react";
```

Import juga `UserContext` yang ada di `ComponentA`

```jsx
import { UserContext } from "./ComponentA";
```

Sekarang `user` context sudah bisa digunakan, tapi sebelumnya state ini harus disimpan lagi kedalam variable:

```jsx
export default function ComponentB() {
  const user = useContext(UserContext)

  ...
}
```

Sekarang state `user` milik `ComponentA` tersimpan didalam variable `const user`, kamu sudah bisa memakainya:

```jsx
export default function ComponentB() {
  const user = useContext(UserContext)

  return (
    <div className="container">
      <p>My name is {user}</p>
    </div>
  );
}
```

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-22