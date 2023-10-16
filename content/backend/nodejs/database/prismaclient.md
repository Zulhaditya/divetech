---
title: Prisma Client
tags:
  - database
---

- Prisma Client merupakan komponen utama di Prisma untuk fitur ORM nya, dimana kita import dari package @prisma/client.
- Prisma Client akan secara otomatis membaca data dari environment variable atau file .env dan juga informasi koneksi database dari prisma schema file.

```js
import { PrismaClient } from "@prisma/client";

describe("Prisma Client", () => {
  it("should be able to connect to database", async () => {
    const prisma = new PrismaClient();
    await prisma.$connect();
    // do something
    await prisma.$disconnect();
  });
});
```

# Jumlah Object Prisma Client

- Saat membuat aplikasi, Prisma Client hanya dibuat sekali saja, bukan berari tiap kita ingin memanipulasi data di database, kita harus membuat Prisma Client.
- Oleh karena itu, sebaiknya kita buat file berisikan variable object Prisma Client, dan jika kita membutuhkannya, cukup ambil dari variable tersebut.

```js
import { PrismaClient } from "@prisma/client";

export const prismaClient = new PrismaClient();
```

# Konfigurasi Prisma Client

- Saat membuat Prisma Client juga, kita bisa menggunakan pengaturan Log untuk Prisma Client.
- https://www.prisma.io/docs/reference/api-reference/prisma-client-reference
- Jika Prisma Client cukup dibuat satu kali, Bagaimana jika aplikasi kita banyak yang membutuhkan koneksi ke database? Prisma Client sudah mengatur jumlah koneksi dalam pool (tempat untuk menyimpan koneksi).
- Kita juga bisa mengatur jumlah koneksi dan timeout pada konfigurasi database url kita.
- https://www.prisma.io/docs/concepts/database-connectors

**Selanjutnya :** [Tag Function](tagfunction.md)
