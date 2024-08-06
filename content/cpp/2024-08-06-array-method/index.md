---
title: Array Method
date: 2024-08-06
weight: 8
tags:
  - C++
---

Array yang di declare dari class memiliki utilitas tambahan daripada array c-style, ini berlaku juga untuk string.

Array/String class memiliki method tambahan untuk mengakses/mengubah atributnya.

## Begin

`std::array::begin`

Mengembalikan nilai awal dari sequence.

```cpp
#include <iostream>
#include <array>

int main ()
{
  std::array<int,5> myarray = { 2, 16, 77, 34, 50 };

  std::cout << "myarray contains:";
  for ( auto it = myarray.begin(); it != myarray.end(); ++it )
    std::cout << ' ' << *it;
  std::cout << '\n';

  return 0;
}
```

## Empty

`std::array::empty`

Mengembalikan nilai `bool`, apakah array kosong atau tidak.

```cpp
// array::empty
#include <iostream>
#include <array>

int main ()
{
  std::array<int,0> first;
  std::array<int,5> second;
  std::cout << "first " << (first.empty() ? "is empty" : "is not empty") << '\n';
  std::cout << "second " << (second.empty() ? "is empty" : "is not empty") << '\n';
  return 0;
}
```