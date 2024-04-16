+++
title = "React Eps II"
draft = false
weight = 3
tags = ['javascript', 'react']
+++

Untuk membuat komponen, ada sebuah general convention yang harus ditaati, yaitu penamaan. Penamaan komponen harus diawali huruf besar.

```plain
|- App.js
|
|- Header.js
|
|- components/
    |
    |- Card.js
    |
    |- Button.js
```

```jsx
// Header.js
function Header() {
  ...
}

export default Header;
```

```jsx
// App.js
import Header from './Header';

function App() {
  return (
    <>
      <Header/>
      ...
    </>
  )
};

export default App;
```

Source Github: https://github.com/ifumikuah/learn-react/tree/eps-ii