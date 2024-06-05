---
title: SQL 13 - Primary Key dan Auto Increment
weight: 13
tags:
  - MySQL
---

Primary key memiliki cara kerja seperti ID, selalu unique. sedangkan Auto Increment berguna untuk auto increment key/id setiap kali dibuat.

```mysql
create table scoreboard (
    user_id int not null auto_increment,
    username varchar(25) unique,
    score int,
    primary key (user_id)
);
```

## Alter

Primary key:

```mysql
ALTER TABLE scoreboard  
ADD PRIMARY KEY (user_id);
```

Untuk mengubah angka mulai auto increment:

```mysql
ALTER TABLE Persons AUTO_INCREMENT=1000;
```

