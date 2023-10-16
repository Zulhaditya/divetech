---
title: Select Fields
tags:
  - database
---

- Saat menggunakan Prisma Client, hampir semua operasi CRUD dan juga findMany() akan melakukan select ke semua field/kolom.
- Lantas bagaimana jika kita ingin membatasi field/kolom yang di select? Kita bisa tambahkan option select ketika melakukan operasi CRUD atau findMany().

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can create and select fields", async () => {
    const customers = await prismaClient.customer.create({
      data: {
        id: "rio",
        email: "riolingga@gmail.com",
        phone: "2727272772",
        name: "Rio Lingga Wijaya",
      },
      select: {
        id: true,
        name: true,
      },
    });
    expect(customers.id).toBe("rio");
    expect(customers.name).toBe("Rio Lingga Wijaya");
    expect(customers.email).toBeUndefined();
    expect(customers.phone).toBeUndefined();
  });

  it("should can select fields", async () => {
    const customers = await prismaClient.customer.findMany({
      select: {
        id: true,
        name: true,
      },
    });
    for (let customer of customers) {
      expect(customer.id).toBeDefined();
      expect(customer.name).toBeDefined();
      expect(customer.email).toBeUndefined();
      expect(customer.phone).toBeUndefined();
    }
  });
});
```

**Selanjutnya :** [Count](count.md)
