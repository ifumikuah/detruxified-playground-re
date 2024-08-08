---
title: "Encapsulation I - Getter"
date: 2024-08-08
weight: 19
tags: [C++]
---

Enkapsulasi adalah salah satu pilar dari OOP, memfokuskan kode pada satu bundling. Ibarat kapsul obat yang bisa menyembuhkan berbagai penyakit dalam sebuah kapsul.

Goal dari enkapsulasi adalah dengan menyembunyikan properti object dari publik, membuat properti tersebut hanya bisa dimodifikasi melalui fungsi-fungsi yang didefinisi di public.

```cpp
class Monke 
{
  private:
    std::name name;
    int banana;
    int level;
}
```

Kita tidak ingin properti tersebut diacak-acak dari luar, maka akan dideklarasi pada *access specifier* `private`. Disini `Monke` adalah mimik sebuah monyet.

Monyet tersebut akan naik level setiap ia makan pisang dalam kuantitas yang ditentukan. Monyet belum memiliki level dan pisang yang dimakan pada saat baru dibuat/spawn.

Pada definisi constuctor:

```cpp
Monke(std::name name)
{
  this->name = name;
  banana = 0;
  level = 0;
}
```

Ingat, Constructor harus ada di public, karena akan di invoke saat pembuatan instansi/object:

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
}
```

## Getter

Getter adalah fungsi yang dibuat bertujuan untuk ekstrak informasi dari properti sebuah object. Getter ini bersifat read-only karena dia hanya return sebuah nilai.

Disebut *getter* karena dia hanyalah sebuah konsep berdasarkan convention, bukan keyword yang tersedia di C++. Membuat getter sama seperti membuat method pada umumnya, biasanya getter tidak menerima parameter karena dia bersifat read only.

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

    std::string getName()
    {
      return name;
    }
}
```

`getName()` adalah sebuah getter yang jika dipanggil akan return nama dari monyetnya.

```cpp
Monke fred("Fred");

std::cout << fred.getName() << std::endl;
```

Membuat getter untuk semua properti akan sangat berguna untuk keperluan loging object nantinya.

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

    std::string getName()
    {
      return name;
    }
    int getBanana()
    {
      return banana;
    }
    int getLevel()
    {
      return level;
    }
}
```

Di halaman [selanjutnya](../2024-08-08-encapsulation-ii/), kita akan membuat mekanism leveling berjalan dengan *setter*.