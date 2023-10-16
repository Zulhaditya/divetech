---
title: Query SQL
tags:
  - database
---

- Prisma Client memiliki method $queryRaw(), yang bisa digunakan untuk mengirim SQL query dengan tujuan mengambil data menggunakan SELECT.
- Return value dari $queryRaw() adalah Promise array yang berisikan data hasil query-nya.
- $queryRaw() menggunakan tag function untuk membuat SQL-nya, dan ini sudah aman dari SQL Injection juga.

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should be able to query sql", async () => {
    const id = "1";
    const samples = await prismaClient.$queryRaw`SELECT * FROM sample WHERE id = ${id}`;

    for (const sample of samples) {
      console.info(`Result sample id: ${sample.id} and name ${sample.name}`);
    }
  });
});
```

**Selanjutnya :** [Prisma ORM](prismaorm.md)
