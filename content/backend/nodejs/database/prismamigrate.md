---
title: Prisma Migrate
tags:
  - database
---

- Prisma memiliki fitur Prisma Migrate, dimana kita bisa membuat database migration untuk membuat schema database menggunakan prisma.
- Keuntungan menggunakan Prisma Migrate, kita tidak perlu mengeksekusi perintah SQL untuk membuat schema database secara manual lagi.

# Mental Model

Sebelum kita membuat migration, kita perlu tahu dua jenis mental model dalam Prisma Migrate yaitu:

- Model/Entity-first migration, yaitu dimana programmer biasa membuat Model terlebih dahulu, lalu Prisma Migrate akan membuatkan perintah SQL DDL nya. Cara ini biasanya digunakan untuk membuat aplikasi baru atau melakukan perubahan baru.
- Database-first migration, yaitu dimana programmer biasa membuat SQL DDL nya terlebih dahulu, menggunakan Prisma Migrate untuk melakukan introspect database untuk membuat model sesuai dengan database. Cara ini biasanya dilakukan ketika menggunakan Prisma untuk database yang sudah ada.

**Selanjutnya :** [Model First Migration](modelfirstmigration.md)
