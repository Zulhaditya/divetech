---
title: Generate
tags:
  - database
---

- Prisma memiliki fitur type safe (beberapa IDE bisa melakukan auto complete), hal ini dikarenakan prisma akan melakukan generate kode dari schema yang kita buat.
- Setiap kita melakukan perubahan kode di file schema prisma, kita harus melakukan perintah:

```bash
npx prisma generate
```

# Membuat Table

- Karena Prisma meminta minimal terdapat model schema, maka kita akan membuat table contoh terlebih dahulu.

```sql
create table sample
(
	id varchar(100) not null,
	name varchar(100) not null,
	primary key (id)
) engine innodb;
```

**Selanjutnya :** [Prisma Client](prismaclient.md)
