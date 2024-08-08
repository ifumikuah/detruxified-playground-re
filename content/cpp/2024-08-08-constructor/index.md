---
title: "Constructor"
date: 2024-08-08
weight: 17
tags: [C++]
---

Sebuah constructor dipanggil otomatis ketika sebuah object dibuat.

```cpp
Human adam;  // memanggil constructor
```

Namun, ada cara yang lebih baik lagi, yaitu dengan memodifikasi constructor sedemikian rupa agar object yang dibuat sesuai dengan yang kita inginkan dengan mendefinisi sendiri constructor tersebut.

```cpp
class Human {
  public:
    std::string name;
    int weight;

    Human(std::string name, int weight)
    {
      this->name = name; // name assigned refers to name in parameter.
      this->weight = weight;
    }
};
```

`this->name` mengacu ke `name` pada object yang sedang dipanggil.

Ketika di invokasi, akan sama seperti biasanya, namun constructur yang digunakan adalah constuctor yang kita definisi tersebut, untuk membuktikan hal ini:

```cpp
class Human {
  public:
    std::string name;
    int weight;

    Human(std::string name, int weight)
    {
      this->name = name; // name assigned refers to name in parameter.
      this->weight = weight+10;
    }
};
```

Buat sebuah instansi dari class tersebut, maka weightnya akan mengikuti definisi di constructor.

```cpp
Human adam("Adam", 77.45);

std::cout << adam.height << "\n"; // 78.45
```

Di definisi constructor, jika nama parameter berbeda dengan properti, `this` tidak perlu digunakan.

```cpp
class Human {
  public:
    std::string name;
    int weight;

    Human(std::string x, int y)
    {
      name = x;
      weight = y;
    }
};
```

## Definisi constructor diluar kelas

Definisi constructor diluar class sama seperti definisi method.

```cpp
class Human {
  public:
    std::string name;
    int weight;

    Human(std::string, int);
};

int main(){...}

Human::Human(std::string x, int y)
{
  name = x;
  weight = y;
}
```

## Membuat instance

Membuat instansi dari class:

```cpp
Human adam("Adam", 76);
```

Menggunakan memori heap:

```cpp
Human *adam;
adam = new Human("Adam", 76);
```