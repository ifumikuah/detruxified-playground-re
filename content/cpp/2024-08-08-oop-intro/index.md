---
title: "Object Oriented Programming intro"
date: 2024-08-08
weight: 16
tags: [C++]
---

C++ adalah impelentasi object oriented programming dari C, superset dari bahasa C.

## Class

`class` adalah keyword yang identik dengan konsep OOP, `class` adalah sebuah data type untuk contructor/blueprint agar kita bisa membuat object yang diinginkan.

```cpp
class Human {
  public:
    std::string name;
    int weight;
};
```

Diatas kita akan membuat sebuah class `Human` mimik objek manusia dengan properti seperti nama dan berat.

`public` adalah access specifier, ibaratnya properti apa saja yang boleh diakses untuk umum, yang pastinya seorang tidak peduli dengan komposisi genetik orang lain kecuali di bidang tertentu.

## Membuat object

Membuat object sama seperti struct, ibaratkan class adalah struct on steroids.

```cpp
class Human {
  public:
    std::string name;
    int weight;
};

int main()
{
  Human adam;

  adam.name = "Adam";
  adam.weight = 78;
}
```

Atau kita bisa membuat object secara dynamic:

```cpp
class Human {
  public:
    std::string name;
    int weight;
};

int main()
{
  Human *adam;
  adam = new Human;

  adam->name = "Adam";
  adam->weight = 78;
}
```

## Method

Manusia bisa berinteraksi dengan sekitarnya, salah satunya adalah berjalan. Method adalah fungsi yang bisa dilakukan pada object tersebut.

```cpp
class Human {
  public:
    std::string name;
    int weight;
  
    void walk()
    {
      std::cout << "walk\n";
    }
};

int main()
{
  Human *adam;
  adam = new Human;

  adam->name = "Adam";
  adam->weight = 78;

  adam->walk();
}
```

Definisi method diluar class.

```cpp
class Human {
  public:
    std::string name;
    int weight;
  
    void walk()
    {
      std::cout << "walk\n";
    }
}

int main() {...}

void Human::walk()
{
  std::cout << "walking...\n";
}
```