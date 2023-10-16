---
title: Intro Prisma
tags:
  - database
---

- Node.js Standard Library tidak menyediakan fitur untuk database.
- Kita akan menggunakan dependency lain, tergantung dari databasenya.

# Database Package

- Ada banyak database package library yang bisa digunakan, tergantung databasenya.
- Hal ini juga menjadi masalah karena akhirnya library databasenya harus diganti jika ingin menggunakan database yang berbeda.
- MySQL: https://www.npmjs.com/package/mysql2
- PostgreSQL: https://www.npmjs.com/package/pg
- Oracle: https://www.npmjs.com/package/oracledb
- Dan lain-lain.

# Masalah dengan Database Package Library

- Karena menggunakan database package library yang terlalu spesifik dengan library yang digunakan, akhirnya kebanyakan programmer Node.js menggunakan library ORM untuk memanipulasi data di database.
- Kita akan menggunakan library ORM untuk memanipulasi data di databasenya.
- Library ORM digunakan agar jika kita ingin mengganti database, kita tidak perlu mengubah kodingannya, akan tetap sama pada setiap database.

**Selanjutnya :** [Pengenalan ORM](introorm.md)
