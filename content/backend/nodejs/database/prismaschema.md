---
title: Prisma Schema
tags:
  - database
---

- Prisma Schema berisikan informasi tentang database yang digunakan oleh Prisma Client, dari mulai koneksi sampai model data.
- Hal ini digunakan untuk men-generate kode Prisma Client.
- Semua detail referensi Prisma Schema bisa kita baca disini:
- https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference

# Model

- Saat kita membuat model di Prisma Schema, kita harus memiliki sebuah field/kolom yang unique (Primary Key).
- Untuk model field, biasanya merepresentasikan nama kolom di table pada database.
- https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#model

# Tipe Data

- Setiap kita menambahkan field di Model, kita harus menentukan tipe data yang akan digunakan.
- Tambahkan tanda tanya (?) pada tipe data tersebut jika tipe data tersebut bisa bernilai null.
- Ada banyak sekali tipe data yang didukung oleh Prisma Schema.
- https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#model-field-scalar-types

# Model Attribute

- Saat kita membuat model, kadang ada informasi tambahan yang perlu kita beritau ke Prisma Schema.
- Contohnya ketika kita ingin membuat nama model berbeda dengan nama table, maka kita gunakan @@map().
- Masih banyak model attribute yang bisa kita gunakan. Kita bisa lihat dokumentasinya di https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#attributes

# Enum

- Di database MySQL dan PostgreSQL, kita bisa membuat tipe data enum.
- Kita juga bisa memberitahu tentang enum di Prisma Schema.
- Kita bisa membuat enum seperti pada dokumentasinya:
- https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#enum

**Selanjutnya :** [Auto Increment](autoincrement.md)
