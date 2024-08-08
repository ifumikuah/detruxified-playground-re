---
title: "Inheritance"
date: 2024-08-08
weight: 21
tags: [C++]
---

Inheritance atau pewarisan adalah salah satu konsep dari OOP. Untuk menguragi redundancy, class bisa mewariskan sifatnya ke sebuah sub-class.

```cpp
class Ape
{
  public:
    std::string name;
    int weight;
};

class Gorilla : public Ape
{
  public:
    bool isCaptive;
};

class Human : public Ape
{
  public:
    std::string religion;
    std::string nationality;
};
```

Diatas, kita membuat sebuah sub-class `Gorilla` dan `Human`. `Ape` akan mewariskan semuanya yang ada di `public` specifier ke sub-classnya.

## Constructor

Pertama, constructor parent (`Ape`) harus dibuat:

```cpp
class Ape
{
  public:
    std::string name;
    int weight;

    Ape(std::string name)
    {
      this->name = name;
    }
};
```

Semua sub-class yang ada dibawah `Ape` memiliki nama.

### Sub-class constructor

Ketika sub-class dipanggil, maka constructor parent di invokasi terlebih dahulu sebelum constructor sub-class nya.

Namun, karena kita menggunakan constructor kita sendiri (bukan default) yang memiliki parameter, maka kita harus mengatur parameter dari constructor tersebut untuk sub-class ini.

```cpp
class Gorilla : public Ape
{
  public:
    bool isCaptive;

    Gorilla(std::string name) : Ape(name)
    {
      isCaptive = false;
    }
};
```

Constructor sub-class `Gorilla` membutuhkan parameter `name` sebagai argument, untuk digunakan ke constructor parent `Ape`.

Hal yang sama juga terjadi untuk `Human`.

```cpp
class Human : public Ape
{
  public:
    std::string religion;
    std::string nationality;

    Human(std::string name, std::string religion, std::string nationality) : Ape(name)
    {
      this->religion = religion;
      this->nationality = nationality;
    }
};
```

## Full code

```cpp
#include <iostream>

class Ape
{
  public:
    std::string name;
    int weight;

    Ape(std::string name)
    {
      this->name = name;
    }
};

class Gorilla : public Ape
{
  public:
    bool isCaptive;

    Gorilla(std::string name) : Ape(name)
    {
      isCaptive = false;
    }
};

class Human : public Ape
{
  public:
    std::string religion;
    std::string nationality;

    Human(std::string name, std::string religion, std::string nationality) : Ape(name)
    {
      this->religion = religion;
      this->nationality = nationality;
    }
};

int main()
{
  using std::cout;

  Human adam("Adam", "Islam", "Turkey");
  Gorilla harambe("Harambe");

  cout << adam.name << "\n";
  cout << harambe.name << "\n";
  cout << harambe.isCaptive << "\n";

  return 0;
}
```