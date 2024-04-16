+++
title = "React Eps VIII"
draft = false
weight = 8
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""
+++

## Conditional Rendering

Rendering komponen secara konditional menggunakan if statement.

```jsx
function WelcomeNotif(props) {
  if (props.username) {
    return <h3 className="welcome-notif login-true">Welcome, {props.username}</h3>
  }
  return <h3 className="welcome-notif login-false">Login required</h3>
};
```
Atau, kita bisa menggunakan ternary.
```jsx
function WelcomeNotif(props) {
  const login = <h3 className="welcome-notif login-true">Welcome, {props.username}</h3>
  const nologin = <h3 className="welcome-notif login-false">Login required</h3>

  return props.username ? login : nologin;
};
```

Kondisi berbeda juga mendapatkan stylingnya masing masing.

```css
.welcome-notif {
  margin: .5rem;
  padding: .3rem 1rem;
  color: #fff;
  font-weight: 400;
  border-radius: 8px;
}

.login-false {
  background-color: #dc3545;
}

.login-true {
  background-color: #198754;
}
```

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-8