---
title: Model First Migration
tags:
  - database
---

- Sebelumnya kita selalu membuat table secara manual, sekarang kita akan buat database baru, dan coba lakukan Model-first migration, dimana kita sudah selesai membuat semua model di Prisma Schema-nya.
- Untuk menjalankan Model-first migration, kita bisa gunakan perintah:

```bash
npx prisma migrate dev --create-only --name nama_migration
```

- Secara otomatis akan dibuatkan file SQL DDL dari model di folder migrations.
- Kita bisa review atau edit terlebih dahulu jika mau, dan pastikan jika ada yang perlu diubah, tidak hanya di SQL DDL, kita juga perlu ubah modelnya.
- Setelah selesai kita jalankan migration menggunakan perintah:

```bash
npx prisma migrate dev
```

# Example

## 1 - Buat database

```sql
CREATE DATABASE belajar_nodejs_prisma;
USE belajar_nodejs_prisma;
```

## 2 - Ganti koneksi di env variable

```env
DATABASE_URL="mysql://ackxle:Aygek6996!@localhost:3306/belajar_nodejs_prisma?connection_limit=5"
```

## 3 - Buat migration script

```bash
npx prisma migrate dev --create-only --name create_all_model
```

## 4 - Lakukan migrate jika data model sudah benar

```bash
npx prisma migrate dev
```

# Tipe Data di Database

- Kadang beberapa jenis tipe data perlu disesuaikan dengan yang ada di database.
- Kita perlu update model sesuai dengan tipe data yang ada di database.
- Kita bisa gunakan attribute di model menggunakan @db.
- Misalkan saat kita gunakan string, tipe data di database bisa saja bukan VARCHAR, oleh karena itu kita beritahu di model prisma-nya.

# Migration Selanjutnya

- Selanjutnya, setiap melakukan perubahan model, kita perlu membuat migration baru.
- Secara otomatis perubahan tersebut akan dibuat SQL DDL nya oleh Prisma Migrate.

# Migration Information

- Prisma Migrate melakukan maintain versi file migrasi yang sudah dieksekusi secara otomatis menggunakan table_prisma_migrations.
- Setiap file migration yang sudah dieksekusi, maka kita tidak boleh mengubahnya lagi, hal ini dikarenakan file migration yang sudah dieksekusi tidak akan pernah dijalankan lagi, jadi percuma saja mengubah file migration lama.
- Selain itu, informasi checksum file migration disimpan di table_prisma_migrations, jadi jika sampai kita ubah, maka akan terjadi error karena checksum nya akan berubah.

**Selanjutnya :** [Database First Migration](databasefirstmigration.md)