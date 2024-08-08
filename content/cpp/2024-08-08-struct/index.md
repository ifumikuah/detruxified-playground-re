---
title: "Structs"
date: 2024-08-08
weight: 14
tags: [C++]
---

Structs di C++ sama seperti di C, namun, di C++ sekarang struct bisa menggunakan default value!!.

```cpp
struct Frame
{
  std::string alias;
  int uid;
  double offset = 1.5;
};


int main()
{
  using std::cout;

  struct Frame *alpha = new Frame;
  alpha->alias = "fermi";
  alpha->uid = 3317;

  cout << alpha->alias << "\n";
  cout << alpha->uid << "\n";
  cout << alpha->offset << "\n";

  delete alpha;
  return 0;
}
```