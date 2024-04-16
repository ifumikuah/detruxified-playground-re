+++
title = "React Eps XV"
draft = false
weight = 15
tags = ['javascript', 'react']
+++

## Updater Functions

### Mempelajari Mekanisme useState()

```jsx
function Cycle() {
  const [counter, setCounter] = useState(0);

  const updater = () => {
    setCounter(counter + 1);
    setCounter(counter + 1);
  };

  return ...
}
```

Hook `useState()` berjalan secara asynchronous, ini artinya ketika kamu memanggil `setCounter(counter + 1)`, `counter` tidak segera diupdate.

Sehingga, jika kamu mambuat panggilan yang sama untuk kedua, ketiga dan seterusnya. Ini sama saja seperti kamu merefresh halaman berkali - kali, `counter` akan tetap bertambah sebanyak 1.

```jsx
const updater = () => {
    setCounter(counter + 1);
    setCounter(counter + 1);
    setCounter(counter + 1);
    setCounter(counter + 1);
  };
```

Ketika kamu mentrigger `updater` diatas, maka counter akan tetap bertambah 1 bukan 4.

### Best Practices

Ada baiknya, jika kamu ingin mendapatkan langsung hasil yang terbaru dari `setCounter`, gunakan sebuah fungsi callback didalam argumen `setCounter` tersebut.

```jsx
function Cycle() {
  const [counter, setCounter] = useState(0);

  const updater = () => {
    setCounter(c => c + 1);
    setCounter(c => c + 1);
    setCounter(c => c + 1);
  };

  return ...
}
```

Diatas, `c` adalah referensi langsung dari nilai `counter` sebelumnya, bukan nilai `counter` sesungguhnya. Dengan ini kamu akan mendapatkan segera nilai terbaru dari `setCounter` sebelumnya.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-15