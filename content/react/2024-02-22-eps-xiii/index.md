+++
title = "React Eps XIII"
draft = false
weight = 13
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "fig2.png"
title = ""

[[resources]]
name = "fig3"
src = "fig3.png"
title = ""
+++

## onChange

`onChange` sama penggunaanya seperti `onClick`, bedanya `onChange` ini merespon ketika ada perubahan terhadap komponen.

Komponen `Form.js` dibawah ini akan menampilkan username yang di input ke element `<p>` secara dinamis
```jsx
// Form.js
import React, {useState} from "react";

function Form() {
  const [username, setUsername] = useState("Unnamed")
  const usernameTrack = (e) => {
    setUsername(e.target.value)
  }

  return (
    <>
      <form>
        <label> Insert Name: &nbsp;
          <input value={username} type="text" placeholder="Unnamed" onChange={usernameTrack}/>
        </label>
      </form>
      <p>Good Morning, {username}</p>
    </>
  )
}

export default Form;
```

{{< img name=fig1 size=small lazy=true >}}

### Menampilkan Option (Dropdown)

```jsx
import React, {useState} from "react";

function Form() {
  const [username, setUsername] = useState("Unnamed")
  const [level, setLevel] = useState("")

  const usernameTrack = (e) => {
    setUsername(e.target.value)
  }
  const levelTrack = (e) => {
    setLevel(e.target.value)
  }

  const styles = {
    display: "flex",
    flexDirection: "column"
  }

  return (
    <>
      <form style={styles}>
        <label>
          <input value={username} type="text" placeholder="Unnamed" onChange={usernameTrack}/>
        </label>

        <label>Level: &nbsp;
          <select onChange={levelTrack}>
            <option value="">Select Level</option>
            <option value="Executive">Executive</option>
            <option value="Specialist">Specialist</option>
            <option value="Supervisor">Supervisor</option>
            <option value="Worker">Worker</option>
          </select>
        </label>

      </form>
      <p>Good Morning, {level} {username}</p>
    </>
  )
}
```

{{< img name=fig2 size=tiny lazy=true >}}

### Menampilkan Radio Button

```jsx
// RadioButtons.js
function RadioButtons() {
  const [fruit, setFruit] = useState("")

  const fruitTrack = (e) => {
    setFruit(e.target.value)
  }

  return (
    <>
      <div className="flex-col">
        <label>
          Apple
          <input type="radio" value="Apple" checked={fruit === "Apple"} onChange={fruitTrack}/>
        </label>

        <label>
          Banana
          <input type="radio" value="Banana" checked={fruit === "Banana"} onChange={fruitTrack}/>
        </label>
      </div>

      <div>
        Selected: {fruit}
      </div>
    </>
  )
};
```

{{< img name=fig3 size=small lazy=true >}}

```jsx
const fruitTrack = (e) => {
    setFruit(e.target.value)
}

<label>
    Banana
    <input type="radio" value="Banana" checked={fruit === "Banana"} onChange={fruitTrack}/>
</label>
```

Ketika terjadi pergerakan/aktivitas di opsi `Banana`, maka `fruitTrack` akan dipanggil dan mengganti value `fruit` menjadi `fruit = "Banana"`.

Aturan `fruit` adalah `"Banana"` memenuhi syarat untuk terpilihnya opsi Banana.

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-13