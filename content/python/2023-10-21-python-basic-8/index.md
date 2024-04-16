+++
title = "Python: List Comprehension"
draft = false
weight = 8
tags = ['python']
+++

Cara singkat untuk membuat/filter sebuah list dan membuatnya di list baru.

```python
ages = [31, 24, 28, 21, 20, 25, 39, 20]
filtered_ages = [x for x in ages if x > 20]
print(filtered_ages)
```

```python
# Syntax
newlist = [expression for item in iterable if condition == True]
```

Filter negara Israel.
```python
countries = ["USA", "UK", "France", "Iraq", "Iran", "Israel", "Japan", "China"]
new_countries = [country for country in countries if country != "Israel"]
print(new_countries)
```

Tambah 50 di setiap data.
```python
number_list = [10, 15, 20, 50, 100, 500]
add_50 = [number + 50 for number in number_list]
```