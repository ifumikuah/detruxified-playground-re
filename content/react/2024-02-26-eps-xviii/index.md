+++
title = "React Eps XVIII"
draft = false
weight = 18
tags = ['javascript', 'react']
+++

## Update Array berisi Object di useState

Ini adalah materi fusion dua episod sebelumnya (eps-xvi dan eps-xvii), menghandle update array yang berisi object.

Pertama, mari membuat sebuah array dengan satu object default (kosong juga boleh):

```jsx
const [list, setList] = useState([{year: new Date().getFullYear(), name: "Adolf"}])
```
Buat juga useState untuk didalam objectnya:
```jsx
const [objName, setObjName] = useState("")
const [objYear, setObjYear] = useState(new Date().getFullYear())
```

Buat juga render elementnya, disini saya hanya menjelaskan fungsi dari setiap `onEvent` dan fungsinya:
```jsx
<ul>
  {list.map((x, id) => <li key={id} onClick={() => delObj(id)}>{x.year}, {x.name}</li>)}
</ul>
<input style={{display: "block"}} type="number" placeholder="year" value={objYear} onChange={handleYearChange}/>
<input style={{display: "block"}} type="text" placeholder="name" value={objName} onChange={handleNameChange}/>
<button onClick={addObj}>SUBMIT</button>
```

### Delete from List

`delObj(id)` ini sama cara kerjanya seperti delete list di episode xvii (lihat pada bagian: Menghapus ikan).

### Onchange Handle Changes

`onChange={handleYearChange}` dan `onChange={handleNameChange}` yang ada pada form, akan mentrigger fungsi dari masing masing input setiap tombol diketik (didalam input).

Dua fungsi ini memiliki task / eksekusi yang sama, mengupdate `objName` dan `objYear` setiap ketikan masuk:
```jsx
const handleNameChange = (ev) => {
  setObjName(ev.target.value)
}
const handleYearChange = (ev) => {
  setObjYear(ev.target.value)
}
```

### Onclick Add Object

`onClick={addObj}` adalah fungsi paling krusial. Fungsi ini menambah hasil input ke object dengan mekanisme yang mirip dengan menambah ikan di episode xvii (lihat pada bagian: Menambah ikan)

```jsx
const addObj = () => {
  if (objName && objYear) {
    const obj = {
      year: objYear,
      name: objName
    }

    setList(l => [...l, obj])
    setObjName("")
    setObjYear(new Date().getFullYear())
  }
}
```

Jika input tidak kosong, maka akan dijalankan.

Hasil kedua input akan ditangkap dan disimpan ke object penampungan sementara `obj`. Lalu dengan cara yang mirip `obj` tersebut ditambah dipaling belakang array spreading yang isinya `list`.

Setelah itu, value input (yang juga merupakan nilai `list`) akan di reset seperti semula.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-18