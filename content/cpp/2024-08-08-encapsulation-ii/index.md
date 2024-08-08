---
title: "Encapsulation II - Setter"
date: 2024-08-08
weight: 20
tags: [C++]
---

Lanjutan dari halaman [sebelumnya](../2024-08-08-encapsulation/). Disini kita akan membuat fungsi untuk level up dengan getter.

Sama seperti getter, setter hanyalah sebuah konsep yang cara kerjanya sama seperti method pada umumnya.

Kita akan membuat sebuah fungsi setter `eat()`. Monyet makan sampai dia melewati batasannya, maka dia akan naik level dan mereset jumlah pisangnya.

```cpp
class Monke 
{
  private:
    std::name name;
    int banana;
    int level;

  public:
    Monke(std::name name)
    {
      this->name = name;
      banana = 0;
      level = 0;
    }

    // Getters
    /*...*/

    // Setters
    void eat()
    {
      banana++;
      if (banana > 10)
      {
        level++;
        banana = 0;
      }
    }
}
```

Mencoba membuat monyet baru:

```cpp
Monke fred("Fred");
fred.eat();
```

Akan sangat berguna jika kita loging data untuk mencegah behavior yang tidak diinginkan terjadi nantinya.

```cpp
class Monke 
{
  private:
    std::name name;
    int banana;
    int level;

  public:
    Monke(std::name name)
    {
      this->name = name;
      banana = 0;
      level = 0;
    }

    // Getters
    /*...*/

    // Setters
    /*...*/

    void log()
    {
      std::cout << "Name    : " << name << "\n";
      std::cout << "Bananas : " << banana << "\n";
      std::cout << "Level   : " << level << "\n";
    }
}
```

Dibawah akan log data setiap Fred memakan 3 buah pisang;

```cpp
Monke fred("Fred");

for (int i = 0; i < 5; i++)
{
  fred.eat();
  fred.eat();
  fred.eat();
  std::cout << "\n";
  fred.log();
}
```