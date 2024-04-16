+++
title = "Python: Intoduction and Basics II"
draft = false
weight = 2
tags = ['python']
+++

Lanjutan dari halaman sebelumnya, kali ini berfokus ke operators.

## Modulo

Tambahan operator matematika yaitu `%` dan `//`.

```python
# Menghasilkan sisa bagi dalam bilangan bulat (modulo)
print(20 % 4)
# Menghasilkan 0

# Menghasilkan hasil pembagian paling mendekati dalam bilangan bulat
print(20 // 6)
# Menghasilkan 3
```

## Exponent

Operator exponent (perpangkatan)

```python
# Menghasilkan 2 pangkat 8 a.k.a jumlah informasi dalam 8bit
print(2 ** 8)
```

## Boolean

| Notation | Compares |
|-|-|
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `>=` | Greater or equal to |
| `<` | Less than |
| `<=` | Less than or equal to |

```python
# Prints True
print(1 == 1)

# Prints True
print(2 + 2 == 4)

# Prints False
print(10 + 9 == 21)

# Prints True
print(10 + 9 != 21)

# Prints False
print(15 + 20 > 20 + 40)

# Prints True
print(35 + 15 <= 25 + 25)
```

### Logical Operators

Kombinasikan dua atau lebih conditional statements (Compare operator).

- `and`
- `or`
- `not`

Untuk melihat table bagaimana ketiga operator bekerja, [lihat disini](https://docs.oracle.com/html/E79061_01/Content/Reference/Truth_tables.htm)

```python
# Evaluates to True
print (2 + 2 == 4 and 1 == 1)
# Evaluates to False
print(10 + 9 == 21 or 15 + 20 > 20 + 40)
# Evaluates to False
print(not 10 + 9 != 21)
```

