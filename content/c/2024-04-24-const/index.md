---
title: Const
date: 2024-04-24
weight: 7
tags: 
  - C
---

`const` adalah nilai konstan, atau variable ini sifatnya immutable/read-only. Variable ini tidak bisa diganti lagi valuenya setelah ditetapkan.

Cocok diimplementasikan, jika kamu ingin sebuah variabel tidak pernah berubah/diubah;

```c
#include <stdio.h>

int main()
{
  const double XV = 23.455555;
  XV = 3.145555;

  printf("%lf", XV);

  return 0;
}
```

{{< hint type="note" title="Hint" >}}

Naming convention untuk variabel `const` adalah dengan memberi huruf besar, walaupun tidak apa-apa menggunakan huruf kecil, namun sangat disarankan untuk menggunakan huruf kapital.

{{< /hint >}}