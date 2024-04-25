---
title: "Project: Circumference"
date: 2024-04-25
weight: 11
tags: 
  - C
---

Mencari keliling lingkaran dengan rumus:

{{< katex display text-center >}}
C = \Pi \cdot d
{{< /katex >}}

```c
// Search for circumference
#include <stdio.h>
#include <math.h>

int main()
{
  const float PI = 3.141593;
  float diameter;

  printf("Insert diameters: ");
  scanf("%f", &diameter); // Don't forget it's reference

  double result = PI * diameter; // Turn to double for more precision

  printf("Circumference is %.2lf", result);

  return 0;
}
```

## Bonus: Hypotenuse finder

```c
// Search for hypotenuse
#include <stdio.h>
#include <math.h>

int main()
{
  float base, perpendicular;

  printf("Insert base and perpendicular: ");
  scanf("%f %f", &base, &perpendicular);

  float hypotenuse = sqrt(pow(base, 2) + pow(perpendicular, 2));

  printf("Circumference is %.2f", hypotenuse);

  return 0;
}
```