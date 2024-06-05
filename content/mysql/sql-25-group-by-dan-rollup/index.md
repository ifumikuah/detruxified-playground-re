---
title: SQL 25 -  Group By dan Rollup
weight: 25
tags:
  - MySQL
---

Group By, membuat group baris yang memiliki value yang sama.

Contoh:

| score_id | score | account_id |
|----------|-------|------------|
|      100 |    30 |          1 |
|      101 |    15 |          1 |
|      102 |     5 |          2 |
|      103 |    10 |          3 |
|      104 |    50 |          2 |
|      105 |    20 |          3 |
|      106 |    25 |       NULL |
|      107 |    10 |       NULL |
|      108 |    10 |       NULL |

```mysql
select account_id, sum(score) from scoreboard
group by account_id;
```

Lihat tabel diatas, beberapa baris memiliki kesamaan, pada `account_id`, merepresentasikan oleh siapa skor ini dicetak (dalam bentuk id).

| account_id | sum(score) |
|------------|------------|
|       NULL |         45 |
|          1 |         45 |
|          2 |         55 |
|          3 |         30 |

## Rollup

Menambah grand total dari group tersebut.

```mysql
select account_id, sum(score) from scoreboard
group by account_id with rollup;
```

| account_id | sum(score) |
|------------|------------|
|       NULL |         45 |
|          1 |         45 |
|          2 |         55 |
|          3 |         30 |
|       NULL |        175 |

Total skor mencapai 175.
