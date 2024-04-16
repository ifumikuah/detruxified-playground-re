+++
title = "Python: Modules"
draft = false
weight = 11
tags = ['python']
+++

Import sebuah fungsi yang ada di file lain sebagai module.

```
Directory Tree
- Py Projects
|
|-- main.py
|
|-- modules.py
```
```py
# Inside of modules.py
def a_function():
    print("This is function")
```

Untuk menggunakan `a_function()` di `main.py`:
```py
# Inside of main.py
from modules import a_function

# Call the function
a_function()
```

Kamu juga bisa mengubah nama fungsi tersebut menjadi yang lain di `main.py` untuk menghindari kebingungan.
```py
from modules import a_function as wowfunc

# Call the function
wowfunc()
```

Import semua fungsi yang ada di `modules`
```py
from modules import *
```

## Built in Modules

Beberapa built in modules sudah ada di python, seperti `random` dan `os`, jadi kamu tinggal import.

```py
import os
import random

# Code goes below
```