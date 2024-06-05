---
title: SQL 5 - Update dan Delete
weight: 5
tags:
  - MySQL
---

	## Warning

Jangan pernah `update` atau `delete` table tanpa keyword `where` setelahnya.
```mysql
update employees
set hourly_pay = 10.50;

select * from employees;
```

Diatas akan mengupdate semua baris dari kolom `hourly_pay` menjadi `10.50`.

atau 
```mysql
delete from employees;

select * from employees;
```

Diatas akan menghapus seluruh baris dari tabel `employees`

## Update tabel

| employee_id | first_name | last_name | hourly_pay | hire_date  |
|-------------|------------|-----------|------------|------------|
| 1           | Arif       | Budiman   | 15.30      | 2024-01-11 |
| 2           | Budi       | Tarmiji   | 10.50      | 2024-01-25 |
| 3           | Joni       | Vercel    | 6.50       | 2024-02-14 |
| 4           | Ellisa     | Jekyll    | 44.50      | 2024-05-25 |
| 5           | Billy      | Netlify   | 2.50       | 2024-04-14 |

Mengupdate `last_name` id `1`:
```mysql
update employees
set last_name = "Tarmiji" 
where employee_id = 1;

select * from employees;
```

## Delete tabel

Delete Ellisa dari employee

```mysql
delete from employees
where first_name = "Ellisa";

select * from employees;
```

Namun, strongly recomended untuk menghapus/edit baris melalui `id`

```sql
delete from employees
where employee_id = 4;

select * from employees;
```

