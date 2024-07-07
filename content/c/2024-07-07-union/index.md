---
title: Union
date: 2024-07-07
weight: 40
tags:
  - C

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

Tipe data **Union** memiliki bentuk yang sama dengan **Struct**, namun behavior yang 180 derajat berbeda. Jika struct bisa menyimpan untuk semua member didalamnya.

```c
struct Structure {
  char name[12]; // 12 bytes
  int number; // 4 bytes
};

printf("%d\n", sizeof(struct Structure)); // 16 bytes
```

Maka **Union** hanya bisa menyimpan untuk satu member didalamnya, yaitu member dengan ukuran paling besar.

```c
union Union
{
  char name[12]; // 12 bytes
  int number; // 4 bytes
};

printf("%d\n", sizeof(union Union)); // 12 bytes
```

## Cara Kerja Union

Setiap member yang ada di union, ter-assign start alamat memory yang sama, dan ending sampai alamat memory yang terbesar member union tersebut punya.

{{< img name=img01 size=large >}}

Member `name` dan `number` diberikan start memory addres yang sama.

Jadi bagaimana jika salah satu dari atau semua member diisi dengan value?. Member yang terakhir diisi value yang akan mendapatkan valuenya tertulis didalam union tersebut.

Union mengalokasikan memori sebesar member yang paling terbesar, namun untuk value yang dibaca adalah value yang terakhir kali di assign oleh kode.

```c
#include <stdio.h>
#include <string.h>

union Uni
{
  char name[12];
  int number;
};


int main(){
  union Uni u;
  strcpy(u.name, "Maxwell");
  u.number = 34;

  printf("%d\n", u.number);
  printf("%s\n", u.name); // memory sudah di overwrite dengan u.number
  return 0;
}
```

Balik urutan assign value `u.number` dan `u.name`, maka kamu akan mendapatkan `u.number` di overwrite oleh `u.name`.

```c
int main(){
  union Uni u;
  u.number = 34;
  strcpy(u.name, "Maxwell");

  printf("%d\n", u.number); // memory sudah di overwrite dengan u.name
  printf("%s\n", u.name);
  return 0;
}
```

## Union use case

Union biasanya digunakan secara *nested* dengan structure, didalam structure tersebut terdapat sebuah union dengan tipe data yang berbeda.

Bayangkan sebuah scenario input number, kemungkinan dua hal terjadi antara user menginput floating number atau non-floating number `int`. Maka kita memerlukan sebuah struct untuk menentukan bilangan input tersebut dan sebuah union yang menyimpan input tersebut.

```c
typedef struct data
{
  int sel; // 0 jika non-floating point, 1 jika floating point
  union
  {
    int nfp; // non-floating point
    double fp; //floating point
  } type;
} number;
```

Lalu membuat handling user input:

```c
int main() {
  char uinput[12];
  number* num; // Pointer to a struct
  num = malloc(sizeof(number)); // Allocate mem. for struct
  num->sel = 0; // Initial type was set to non-floating point

  printf("insert number: ");
  scanf("%s", uinput);

  //...
}
```

Jika input berupa string didapatkan, maka if statements untuk menentukan bilangan tersebut dimulai.

```c
if (strchr(uinput, '.') != NULL)
    num->sel = 1;
```

Diatas akan check apakah input mengandung koma, jika iya maka tipe yang dimasukkan adalah floating point. Lalu output data tersebut sesuai tipe datanya.

```c
if (num->sel)
{
  num->type.fp = atof(uinput);
  printf("%lf\n", num->type.fp);
} 
else
{
  num->type.nfp = atoi(uinput);
  printf("%d\n", num->type.nfp);
}
```

### Full Code

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct data
{
  int sel;
  union
  {
    int nfp;
    double fp;
  } type;
} number;


int main() {
  char uinput[12];
  number* num;
  num = malloc(sizeof(number));
  num->sel = 0;

  printf("insert number: ");
  scanf("%s", uinput);
  
  if (strchr(uinput, '.') != NULL)
    num->sel = 1;
  
  if (num->sel)
  {
    num->type.fp = atof(uinput);
    printf("%lf\n", num->type.fp);
  } 
  else
  {
    num->type.nfp = atoi(uinput);
    printf("%d\n", num->type.nfp);
  }
  
  free(num);
  return 0;
}
```