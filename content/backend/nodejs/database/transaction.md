---
title: Transaction
tags:
  - database
---

- Di Prisma Client, kita bisa menggunakan method $transaction() untuk melakukan transaksi.
- Jika satu transcation gagal maka akan kita gagalkan semua, jika sukses harus sukses semuanya.
- Terdapat dua mekanisme untuk melakukan transaksi di Prisma Client:
- Sequential Transaction: kita bisa mengirim semua operasi di Prisma Client sebagai Array.
- Interactive Transaction: kita bisa menggunakan callback function yang berisikan kode transaksinya.

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  // sequential transaction
  it("should can exectute sequential transaction", async () => {
    const [goku, naruto] = await prismaClient.$transaction([
      prismaClient.customer.create({
        data: {
          id: "goku",
          name: "Goku",
          email: "goku@gmail.com",
          phone: "12233333",
        },
      }),
      prismaClient.customer.create({
        data: {
          id: "naruto",
          name: "Naruto",
          email: "naruto@gmail.com",
          phone: "22222333",
        },
      }),
    ]);
    expect(goku.name).toBe("Goku");
    expect(naruto.name).toBe("Naruto");
  });

  // interactive transaction
  it("should can exectute interactive transaction", async () => {
    const [goku, naruto] = await prismaClient.$transaction(async (prisma) => {
      const goku = await prisma.customer.create({
        data: {
          id: "goku2",
          name: "Goku",
          email: "goku2@gmail.com",
          phone: "122329933",
        },
      });
      const naruto = await prisma.customer.create({
        data: {
          id: "naruto2",
          name: "Naruto",
          email: "naruto2@gmail.com",
          phone: "2229897233",
        },
      });
      return [goku, naruto];
    });
    expect(goku.name).toBe("Goku");
    expect(naruto.name).toBe("Naruto");
  });
});
```

**Selanjutnya :** [CRUD Many](crudmany.md)
