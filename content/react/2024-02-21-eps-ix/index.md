+++
title = "React Eps IX"
draft = false
weight = 9
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""
+++

## Default Value

Membuat sebuah default value dari props di komponen

```jsx
function WelcomeNotif(props) {
  const login = <h3 className="welcome-notif login-true">Welcome, {props.username}</h3>
  const nologin = <h3 className="welcome-notif login-false">Login required</h3>

  return props.login ? login : nologin;
};

WelcomeNotif.defaultProps = {
  login: false,
  username: "Guest"
}
```

Percobaan di App.js

```jsx
...
  <WelcomeNotif login={true} username="Simon"/>
  <WelcomeNotif login={true}/>
  <WelcomeNotif/>
...
```

{{< img name=fig1 size=medium lazy=true >}}

Github Source: https://github.com/ifumikuah/learn-react/tree/eps-9