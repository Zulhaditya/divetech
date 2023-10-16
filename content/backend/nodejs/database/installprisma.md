---
title: Install Prisma
tags:
  - database
---

- Untuk menginstall Prisma, kita bisa menggunakan perintah:

```bash
npm install prisma --save-dev
```

- Selanjutnya kita tidak bisa langsung menjalankan Prisma, kita perlu melakukan pengaturan terlebih dahulu menggunakan Prisma CLI dengan perintah:

```bash
npx prisma
```

# Membuat Project Prisma

- Untuk membuat project prisma untuk pertama kali, kita perlu menggunakan perintah:

```bash
npx prisma init
```

- Secara otomatis Prisma akan membuat file:
- .env yang berisikan konfigurasi environment variable.
- prisma/schema.prisma, yang berisikan schema pemetaan dengan database.

**Selanjutnya :** [Database Connection](databaseconnection.md)