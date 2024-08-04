---
title: Namespace
date: 2024-08-04
weight: 2
tags:
  - C++
---

C++ memperkenalkan `namespace`, sebuah identifier. Namun apa urgency dari `namespace`?

Bayangkan ada dua nama fungsi yang sama dengan konteks/definisi yang berbeda.

```cpp
void print()
{
  std::cout << "Print x";
}

void print()
{
  std::cout << "Print y";
}
```

`namespace` mengeliminasi masalah ini dengan memberikan indentifier pada masing masing fungsi.

```cpp
namespace alpha
{
  void print()
  {
    std::cout << "Print x";
  }
}

namespace beta
{
  void print()
  {
    std::cout << "Print y";
  }
}
```

lalu kita bisa menggunakannya.

```cpp
alpha::print();
beta::print();
```