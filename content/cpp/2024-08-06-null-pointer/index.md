---
title: "Dynamic memory in C++"
date: 2024-08-06
weight: 12
tags: [C++]
---

Alokasi memori di C++ berbeda tapi serupa dengan yang ada di C, jika C menggunakan fungsi `malloc()`, maka C++ menggunakan sebuah operator `new`.

## Declare memory allocation

```c
/*C way*/
int* ptr;
ptr = (int*) malloc(sizeof(int));

*ptr = 10;
```

```cpp
/*C++ way*/
int* ptr;
ptr = new int;

*ptr = 10;
```

## Null pointer

Null pointer di C++ bukan lagi `NULL` seperti di C, namun diganti menjadi keyword `nullptr` berjenis `std::nullptr_t`.

```cpp
char* placeholder = nullptr;

if (placeholder == nullptr)
{
  std::cout << "placeholder is empty!!" << std::endl;
}
```

## Pointer for array

Jika ingin alokasi untuk array dinamis, membuat array sebesar 5 integer:

```cpp
int* ptr;
ptr = new int[5];

for (int i = 0; i < 5; i++)
  *(ptr+i) = (i+1)*2; // fill array to {2, 4, 6, 8, 10}
```

## Multidimensional dynamic array

```cpp
int** ptr;
ptr = new int*[4] // 4 row

for (int i = 0; i < 4; i++)
{
  ptr[i] = new int[2] // 2 column
}
```

Deklarasi array dinamis diatas sama dengan:

```cpp
int array[4][2];
```

Lalu kita bisa mengisi array tersebut seperti biasa:

```cpp
for (int i = 0; i < 4; i++)
{
  for (int j = 0; j < 2; j++)
  {
    array[i][j] = (i+1)*(j+1);
  }
}
```

## Free allocated memory

Membebaskan memori di C++ menggunakan keyword `delete`.

```cpp
delete ptr;
```

Menghapus memori yang dialokasikan di array multidimensional tadi:

```cpp
for (int i = 0; i < row; i++)
  delete array[i];

delete array;
```

Memori yang dialokasikan menggunakan `new` harus dibebaskan menggunakan `delete`, hal yang sama juga terjadi jika alokasi menggunakan `malloc()` yang harus dibebaskan dengan `free()`.