---
date: '2024-12-09'
draft: false
tags: [teknologi, c]
title: Queue data structures
weight: 15
resources:
- name: img01
  src: "img/img01.png"
  title: ""
- name: img02
  src: "img/img02.png"
  title: ""
- name: img03
  src: "img/img03.png"
  title: ""
- name: img04
  src: "img/img04.png"
  title: ""
---

Queue, kebalikan dari stack, adalah data structure yang bekerja seperti antrian, (FIFO) *First In First Out*.

Implementasi kan queue didalam bahasa C, maka kita menggunakan array, mari mulai dengan array kecil `arr[3]`.

{{< img name=img01 size=small >}}

Tidak seperti stack yang hanya memiliki 1 "lubang", queue memiliki 2 lubang untuk masuk dan untuk keluar yang berbeda, yaitu `start` dan `end`.

Sebuah queue dimulai dari queue kosong, maka dari itu kita mulai dari `-1` sebagai indikasi kosong. Jika nilai `start` dan/atau `end` bukan `-1`: indikasi tidak kosong.

Ada 4 operasi penting didalam queue:

- isEmpty
- Enqueue
- Peek
- Dequeue

## isEmpty

Mengecek apakah queue kosong. Jika iya, nilai `true`.

Syarat agar queue kosong adalah satu: `start` dan `end` sama-sama bernilai `-1`, maka:

```cpp
bool isempty()
{
  return start == -1 && end == -1 ? true : false;
}
```

## Enqueue

Tambahkan ke antrian.

Pertama yang dilakukan adalah sebuah *switch*, eksekusi nilai `start` dan `end` menjadi `0` jika sebelumnya kosong. Jika tidak, maka kita hanya perlu menambah nilai `end` saja:

```cpp
void enqueue(int data)
{
  if (isempty())
    start = end = 0;
  else
    end++;
  arr[end] = data;
}
```

Ini yang terjadi jika sebelumnya queue kosong:

{{< img name=img02 size=small >}}

Jika sebelumnya diisi:

{{< img name=img03 size=small >}}


## Peek

"Mengintip" antrian paling depan/awal, dalam hal ini `start`.

```cpp
int peek()
{
  return arr[end];
}
```

## Dequeue

Keluarkan item paling awal dari antrian.

Maka nilai `start` akan bertambah jika dikeluarkan dari antrian, nilai `start` menjadi index dari item selanjutnya. Namun, sebelumnya kita perlu pengecekan untuk antrian terakhir...

Antrian terakhir maksudnya adalah item tersebut satu-satunya didalam queue tersebut, artinya `start` dan `end` sama, jika iya, maka `dequeue()` akan mengganti nilai `start` dan `end` menjadi `-1`, alias kosong.

Jika kosong, maka tidak melakukan apapun.

```cpp
void dequeue()
{
  if (isempty()) return;
  if (start == end)
  {
    start = end = -1;
  }
  else
  {
    start++;
  }
}
```

{{< img name=img04 size=small >}}