---
title: "Default parameter"
date: 2024-08-08
weight: 15
tags: [C++]
---

Kita bisa assign default parameter di C++ dengan `=`.

```cpp
int sum (int n1 = 1, int n2 = 1)
{
  return n1+n2;
}

int main()
{
  std::cout << sum(3) << std::endl;
  return 0;
}
```

Namun, jika kamu menggunakan prototype fungsi, default parameter harus terletak pada bagian deklarasi saja.

```cpp
int sum (int n1 = 1, int n2 = 1);

int main()
{
  std::cout << sum(3) << std::endl;
  return 0;
}

int sum (int n1, int n2)
{
  return n1+n2;
}
```

## Overloading

Menggunakan default parameter pada deklarasi fungsi yang di overload bisa saja membuat panggilan fungsi menjadi ambigu pada saat kompilasi.

```cpp
int main(){...}

int sum(int n1, int n2, int n3 = 0, int n4 = 0)
{
  return n1+n2+n3+n4;
}

int sum(int n1, int n2, double n3 = 0, double n4 = 0)
{
  return n1+n2+n3+n4;
}
```

Melihat hanya parameter dengan default value yang memiliki tipe berbeda membuat kompiler akan kebingungan saat evaluasi panggilan.

```cpp
int s1 = sum(3, 4, 1.5);
```

Pemanggilan diatas dievaluasi secara baik karena kompiler menemukan sebuah tipe data double dan sudah tau seharusnya definisi yang mana akan dipakai.

Bagaimana dengan ini:

```cpp
int s1 = sum(3, 4);
```

Kompiler kebingungan harus memilih definisi karena keduanya cocok dengan kriteria panggilan fungsi tersebut. Jadi pastikan kode bebas dari keambiguan.