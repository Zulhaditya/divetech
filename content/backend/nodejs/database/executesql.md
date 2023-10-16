---
title: Execute SQL
tags:
  - database
---

- Prisma Client memiliki method $executeRaw(), yang digunakan untuk mengirim data SQL dengan tujuan memanipulasi data seperti INSERT, UPDATE atau DELETE.
- Return value dari $executeRaw() adalah Promise Number yang berisikan jumlah data yang terkena impact dari operasi SQL yang kita lakukan.
- Method $executeRaw menggunakan Tag Function untuk membuat SQL-nya, dan ini sudah aman dari SQL Injection, sehingga kita tidak perlu takut orang mengirim data yang berbahaya yang bisa membuat kode SQL kita rusak.

**Selanjutnya :** [Query SQL](querysql.md)
