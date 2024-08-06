---
title: Getline
date: 2024-08-06
weight: 9
tags:
  - C++
---

Kita mendapatkan karakter menggandung spasi memiliki behavior aneh jika berasal dari input stream seperti `std::cin`.

```cpp
std::string strbuf;

std::cout << "Insert fullname: ";
std::cin >> strbuf;

std::cout << "Hello, " << strbuf << std::endl;
```

## Getline

`getline` bisa mengatasinya, getline akan membaca seluruh karakter dalam sequence sampai endline `\n` atau `\0` ditemukan.

```cpp
std::string strbuf;

std::cout << "Insert fullname: ";
getline(std::cin, strbuf);

std::cout << "Hello, " << strbuf << std::endl;
```