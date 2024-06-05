---
title: SQL 17 - Logical operator
weight: 17
tags:
  - MySQL
---

Logical operator di mysql ada: `AND`, `OR`, `NOT`.

## AND

```mysql
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition1_ AND _condition2_ AND _condition3 ..._;
```

## OR

```mysql
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition1_ OR _condition2_ OR _condition3 ..._;
```

## NOT

```mysql
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE NOT _condition_;
```
