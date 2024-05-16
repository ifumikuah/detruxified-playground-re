---
title: Array of strings
date: 2024-05-16
weight: 21
tags: 
  - C
---

Sebuah string adalah array dari `char`, jadi string yang ada dalam array adalah array 2 dimensi.

```c
char cities[3][10] = {"Jerusalem", "Hebron", "Nablus"};
```

Masing masing string didalam array dialokasikan sebesar 10x char didalamnya. Jika sebuah char adalah 1 byte (8bit), maka array `cities` ini memakan 3*10 byte (30 bytes).

`{"Jerusalem", "Hebron", "Nablus"}` Jika dihitung total charnya hanya memakan 21 karakter, artinya 21 bytes dipakai oleh program sebenarnya, meninggalkan 9 byte terbuang sia-sia oleh array ini, fenomena ini disebut dengan **Memory Wastage**.

## Manipulasi array

Manipulasi array string berbeda dari biasanya.

```c
// Hasilnya akan error
cities[0] = "Rafah";
```

Gunakan `strcpy()` dari `string.h` untuk manipulasi element didalam array string.

```c
strcpy(cities[0], "Rafah");
```

## Loop array

```c
for (int i = 0; i < sizeof(cities)/sizeof(cities[0]); i++)
{
  printf("%s\n", cities[i]);
}
```