---
title: "Constructor overloading"
date: 2024-08-08
weight: 18
tags: [C++]
---

Overloading constructor sama halnya seperti overloading fungsi.

```cpp
class Human {
  public:
    std::string name;
    double height; 
    double weight;

    Human(std::string name)
    {
      this->name = name;
    }
    Human(std::string name, double height)
    {
      this->name = name;
      this->height = height;
    }
    Human(std::string name, double height, double weight)
    {
      this->name = name;
      this->height = height;
      this->weight = weight;
    }
};
```

Untuk definisi diluar class, sama seperti biasanya.

Pembuatan object:

```cpp
int main()
{
  using std::cout;

  Human* eve;
  eve = new Human("Eve", 167.88);

  cout << eve->name << "\n";
  cout << eve->height << "\n";
  cout << eve->weight << "\n";

  return 0;
}
```