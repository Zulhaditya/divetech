---
title: Model
tags:
  - database
---

- Saat membuat table di database, kita perlu membuat model di Prisma, hal ini agar kode untuk memanipulasi data model tersebut di generate oleh Prisma CLI sehingga bisa digunakan menggunakan Prisma Client.
- Untuk membuat model, kita bisa membuat model Prisma Schema.
- Nama model akan menjadi nama table di database, jika kita ingin mengubahnya, kita bisa gunakan @@map("namatable").
- Kolom yang boleh null, kita perlu tandai dengan ? (tanda tanya).
- Untuk kolom primary key, perlu kita tandai dengan @id.
- Setelah mengubah model, jangan lupa untuk generate prisma client menggunakan perintah:

```bash
npx prisma generate
```

```js
model Customer {
id String @id
name String
email String @unique
phone String @unique
@@map("customers")
}
```

```sql
CREATE TABLE
customers (
id varchar(100) not null,
name varchar(100) not null,
email varchar(100) not null,
phone varchar(100) not null,
primary key (id),
constraint customers_email_unique unique (email),
constraint customers_phone_unique unique (phone)
) engine innodb;
SELECT
*
FROM customers;
```

**Selanjutnya :** [CRUD](crud.md)