---
title: CRUD
tags:
  - database
---

- Setelah membuat generate code dari Model, secara otomatis kita bisa melakukan operasi CRUD (CREATE, READ, UPDATE, DELETE) menggunakan Prisma Client.
- Prisma Client otomatis memiliki field dengan nama model yang kita buat dalam lowercase, misalkan sebelumnya kita menggunakan nama model Customer, maka akan dibuatkan field PrismaClient.customer yang merupakan Prisma Model Query.
- https://www.prisma.io/docs/reference/api-reference/prisma-client-reference#model-queries

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  // Create Customer
  it("should be able to create customer", async () => {
    const customer = await prismaClient.customer.create({
      data: {
        id: "inayah",
        email: "inayah@gmail.com",
        name: "Inayah",
        phone: "081232123444",
      },
    });
    expect(customer.id).toBe("inayah");
    expect(customer.email).toBe("inayah@gmail.com");
    expect(customer.name).toBe("Inayah");
    expect(customer.phone).toBe("081232123444");
  });

  // Update Customer
  it("should be able to update customer", async () => {
    const customer = await prismaClient.customer.update({
      data: {
        name: "Inayah Fitri Wulandari",
      },
      where: {
        id: "inayah",
      },
    });
    expect(customer.id).toBe("inayah");
    expect(customer.email).toBe("inayah@gmail.com");
    expect(customer.name).toBe("Inayah Fitri Wulandari");
    expect(customer.phone).toBe("081232123444");
  });

  // Read Customer
  it("should be able to read customer", async () => {
    const customer = await prismaClient.customer.findUnique({
      where: {
        id: "inayah",
      },
    });
    expect(customer.id).toBe("inayah");
    expect(customer.email).toBe("inayah@gmail.com");
    expect(customer.name).toBe("Inayah Fitri Wulandari");
    expect(customer.phone).toBe("081232123444");
  });

  // Delete Customer
  it("should be able to delete customer", async () => {
    const customer = await prismaClient.customer.delete({
      where: {
        id: "inayah",
      },
    });
    expect(customer.id).toBe("inayah");
    expect(customer.email).toBe("inayah@gmail.com");
    expect(customer.name).toBe("Inayah Fitri Wulandari");
    expect(customer.phone).toBe("081232123444");
  });
});
```

**Selanjutnya :** [Transaction](transaction.md)
