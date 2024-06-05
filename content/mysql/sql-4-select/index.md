---
title: SQL 4 - Select
weight: 4
tags:
  - MySQL
---

Katakan kamu memiliki tabel `employees`:

| employee_id | first_name | last_name | hourly_pay | hire_date  |
|-------------|------------|-----------|------------|------------|
| 1           | Arif       | Budiman   | 15.30      | 2024-01-11 |
| 2           | Budi       | Tarmiji   | 10.50      | 2024-01-25 |
| 3           | Joni       | Vercel    | 6.50       | 2024-02-14 |
| 4           | Ellisa     | Jekyll    | 44.50      | 2024-05-25 |
| 5           | Billy      | Netlify   | 2.50       | 2024-04-14 |

## Select berdasarkan value table

```mysql
select * from employees
where last_name = "Tarmiji";
```

| employee_id | first_name | last_name | hourly_pay | hire_date  |
|-------------|------------|-----------|------------|------------|
| 2           | Budi       | Tarmiji   | 10.50      | 2024-01-25 |

Select kolom nama pertama dari "Tarmiji":

```mysql
select first_name from employees
where last_name = "Tarmiji";
```

Select beberapa detail dari "Tarmiji":

```mysql
select first_name, last_name, hourly_pay from employees
where last_name = "Tarmiji";
```

## Select menggunakan logical operator

Misal ingin mencari karyawan bergaji > 10:
```mysql
select * from employees
where hourly_pay > 10;
```

Atau gaji dibawah sama dengan 15,30:
```mysql
select * from employees
where hourly_pay <= 15.30;
```

Mencari karyawan yang **Tidak** memiliki nama belakang "Tarmiji":
```mysql
select * from employees
where last_name != "Tarmiji";
```

## IS dan NOT

Mencari karyawan yang `hire_date` = `null` atau kosong:
```mysql
select * from employees
where hire_date is null;
```

Mencari karyawan yang `hire_date` tidak kosong:
```mysql
select * from employees
where hire_date is not null;
```
