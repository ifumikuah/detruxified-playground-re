---
title: String?
date: 2024-04-23
weight: 3
tags: 
  - C
---

Apakah ada tipe data `string` di C?, jawabannya **tidak**.

Tapi kita bisa "mengakalinya" dengan representasi sebuah array. Jadi sebuah array yang terdiri dari char-char.

{{< hint type="note" title="Fun Fact" >}}
"Pengakalan" ini bisa dibuktikan jika kamu familiar dengan bahasa high-level sebelumnya.

Contoh di JavaScript dan Python yang mana sintaksnya berdasarkan bahasa C, kamu bisa mengakses sebuah karakter dalam sebuah tipe data `string` melalui indexnya.

Yang mana artinya datatype `string` ini sendiri merupakan kumpulan karakter dalam sebuah 'array' pada akhirnya.
{{< /hint >}}

Tipe data ini termasuk kedalam kategori `array` dengan format specifier `%s`

```c
int main()
{
  char animal[] = "Horse";
  printf("Running %s", animal);

  return 0;
}
```