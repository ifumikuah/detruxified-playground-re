---
title: Console Input
date: 2024-08-04
weight: 4
tags:
  - C++
---

Membaca input dari console.

`cin` tesedia melalui `iostream`, sama halnya seperti `cout`.

`cout` menggunakan operator *stream insertion* [<<](https://en.cppreference.com/w/cpp/io/basic_ostream/operator_ltlt), memasukkan data ke stream.

maka sebaliknya `cin` menggunakan *stream extraction* [>>](https://en.cppreference.com/w/cpp/io/basic_istream/operator_gtgt), ekstrak data dari stream.

```cpp
int x;

cout << "Value: ";
cin >> x;

cout << x;
```

## Input string

```cpp
std::string usernm;

std::cout << "Username: ";
std::cin >> usernm;

std::cout << "Hi " << usernm;
```

`std::string` adalah sebuah object yang menampung `usernm`.

Namun, terdapat kelemahan pada kode diatas, jika kamu memasukkan string dengan spasi (whitespace), karena operator `>>` langsung terminasi pembacaan string ketika jumpa whitespace.

Kita menggunakan `std::getline` untuk membaca string mengandung spasi.

```cpp
std::string fullname;

std::cout << "Full Name: ";
std::getline(std::cin, fullname);

std::cout << "Hi " << fullname;
```

`getline(std::cin, fullname)` akan ekstrak data dari stream `cin` lalu diletakkan ke `fullname`.