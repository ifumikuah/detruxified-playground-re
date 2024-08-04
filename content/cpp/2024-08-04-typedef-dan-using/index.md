---
title: Typedef dan using
date: 2024-08-04
weight: 3
tags:
  - C++
---

`typedef` dan `using` memiliki tujuan yang sama, hanya saja `typedef` sudah ada dari dulu di bahasa C, ketimbang `using` yang baru diperkenalkan di C++.

Penggunaan `typedef`:

```cpp
typedef unsigned short int sint_t;

int main()
{
  sint_t vars = 43;
}
```

Penggunaan `using`:

```cpp
using sint_t = unsigned short int;

int main()
{
  sint_t vars = 43;
}
```

Namun, `using` lebih disarankan ketimbang `typedef` jika kamu berada di C++.

```cpp
using std::cout;
using sint_t = unsigned short int;

int main()
{
  sint_t vars = 43;
  cout << vars;
}
```

[Referensi using](https://en.cppreference.com/w/cpp/keyword/using).