---
title: "Bracket balance check: balance algorithm"
date: 2024-08-09
description: "Stack"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
- name: img02
  src: "img/img02.png"
  title: ""
---

Jika seimbang, visual program seharusnya berjalan seperti ini:

{{< img name=img02 size=medium >}}

Sebaliknya, visual program akan menjadi seperti ini:

{{< img name=img01 size=medium >}}

Main algoritma program adalah seperti ini:

```c
if (isempty(&tmp_stack))
{
  push(&tmp_stack, test[i]);
}
else if ( test[i] == ']' && peek(&tmp_stack) == '[' ||
          test[i] == ')' && peek(&tmp_stack) == '(' ||
          test[i] == '}' && peek(&tmp_stack) == '{' )
{
  pop(&tmp_stack);
}
else
{
  push(&tmp_stack, test[i]);
}
```

## Full code


```c
#include <stdio.h>
#include <stdbool.h>

typedef struct Stack
{
  char array[24];
  int size;
} Stack;

void push(Stack*, char);
void pop(Stack*);
char peek(Stack*);
bool isempty(Stack*);

int main(int argc, char** argv)
{
  Stack tmp_stack;
  tmp_stack.size = -1;

  char* test = "()[{[][()]}]";
  bool isbalance = true;

  for (int i = 0; test[i] != '\0'; i++)
  {
    if (isempty(&tmp_stack))
    {
      push(&tmp_stack, test[i]);
    }
    else if ( test[i] == ']' && peek(&tmp_stack) == '[' ||
              test[i] == ')' && peek(&tmp_stack) == '(' ||
              test[i] == '}' && peek(&tmp_stack) == '{' )
    {
      pop(&tmp_stack);
    }
    else
    {
      push(&tmp_stack, test[i]);
    }
  }
  isbalance = isempty(&tmp_stack);

  printf("%d\n", isbalance);
  return 0;
}

void push(Stack* stack, char value)
{
  stack->size++;
  stack->array[stack->size] = value;
}

void pop(Stack* stack)
{
  if (stack->size < 0)
    return;

  stack->size--;
}

char peek(Stack* stack)
{
  return stack->array[stack->size];
}

bool isempty(Stack* stack)
{
  return stack->size < 0;
}
```