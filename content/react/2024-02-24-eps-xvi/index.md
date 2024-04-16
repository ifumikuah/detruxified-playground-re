+++
title = "React Eps XVI"
draft = false
weight = 16
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""
+++

## Update Object di useState

Untuk mengupdate object di state relatif mudah. Pertama kita siapkan sebuah object sebagai dafault state dulu.

```jsx
// Kamu juga bisa menyimpan object tersebut kedalam sebuah variable
const [aircraft, setAircraft] = useState({model: "777-200ER", manufacturer: "Boeing", year: 1998})
```

Lalu juga membuat element untuk rendering.

```jsx
// Contoh ini hanya mengubah manufaktur pesawat
return (
    <>
      <h2>{aircraft.year}, {aircraft.manufacturer} {aircraft.model}</h2>
      <form>
        <label style={{display: "block"}}>Enter manufacturer &nbsp;
          <input type="text" value={aircraft.manufacturer}/>
        </label>
      </form>
    </>
  )
```

### Fungsi update object

Di javascript, object tidak bisa menerima key yang serupa, jika ada yang serupa maka yang paling belakang menjadi nilai/value dari key tersebut.

```js
const plane = {
  model: "S.XIII", 
  manufacturer: "SPAD", 
  year: 1918,
  model: "XVII"
}
```

Maka `plane.model` adalah `XVII` dan kita bisa gunakan ini untuk mengupdate object kita.

Membuat fungsi untuk update manufaktur `setAircraft`:

```jsx
const setAircraftManufacturer = (event) => {
    setAircraft({...aircraft, manufacturer: event.target.value})
  }
```

Diatas akan *spread* isi dari object aircraft ke object tersebut, dan key `model` yang ada setelahnya berfungsi untuk update `model` dari pesawat.

Jadi kasarnya akan menjadi seperti ini:

```js
{model: "777-200ER", manufacturer: "Boeing", year: 1998, manufacturer: event.target.value}
```

{{< img name=fig1 size=medium lazy=true >}}

### Updater Function

Fungsi diatas sudah berfungsi, namun sebaiknya kita menggunakan updater function untuk keamanan.

```jsx
  const setAircraftManufacturer = (event) => {
    setAircraft(
      a => ({...a, manufacturer: event.target.value})
    )
  }
```

Implicit return harus menggunakan kurung jika ingin return objek, kalau tidak akan dikira oleh javascript sebagai bracket explicit return.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-16