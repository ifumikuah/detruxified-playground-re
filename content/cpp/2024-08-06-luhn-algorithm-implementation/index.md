---
title: "Implementasi luhn algorithm di C++"
date: 2024-08-06
weight: 11
tags: [C++]

resources:
- name: "img01"
  src: "img/img01.png"
  title: ""
---

Luhn algorithm digunakan untuk validasi ID Numerik seperti kartu kredit, algoritma ini hanya digunakan untuk melindungi kesalahan input, bukan serangan yang disengaja.

Ada 4 step dalam algoritma Luhn:

1. Gandakan angka yang ada pada posisi **genap** dari kanan ke kiri.
2. Jika angka hasil ganda tersebut diatas sembilan, maka kurangi sembilan.
3. Angka pada posisi **genap** telah berubah, maka jumlahkan semuanya.
4. Jika hasilnya habis dibagi sepuluh, maka ID valid.

{{< img name=img01 size=small >}}

Implementasinya di C++:

```cpp
bool luhn_test(const std::string cc)
{
  int sum = 0;

  for (int i = cc.length()-1; -1 < i; i--)
  {
    int digit = cc[i]-'0';
    if ((cc.length() - i) % 2 == 0)
    {
      digit *= 2;
      if (digit > 9)
        digit -= 9;

      sum += digit;
    }
    else
    {
      sum += digit;
    }
  }

  return sum % 10 == 0;
}
```

