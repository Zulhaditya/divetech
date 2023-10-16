---
title: CRUD Many
tags:
  - database
---

- Sebelumnya kita telah mempelajari tentang CRUD menggunakan Prisma Client.
- Namun hanya untuk satu data.
- Prisma Client juga mendukung fitur CRUD lebih dari satu data, kita bisa menggunakan method suffix many.

# Update Many

- Update many di Prisma Client bukan dengan mengirimkan banyak data, lalu data tersebut di-update satu persatu.
- Update many di Prisma Client adalah operasi update, yang bisa berdampak ke banyak data.
- Lalu apa bedanya dengan update single? bedanya untuk update single, Prisma akan melakukan query terlebih dahulu untuk memastikan bahwa cuma ada 1 data yang tersedia, dan untuk query-nya pun hanya bisa di primary key atau unique colom.
- Sedangkan di Update many, kita bisa update dengan query pada kolom apapun, karena bisa berdampak pada banyak data.

# Delete Many

- Delete many juga sama dengan update many, dimana kita bisa melakukan operasi delete yang bisa berdampak ke banyak data.
- Perbedaan delete single adalah sama seperti update single, Prisma Client akan melakukan select terlebih dahulu untuk memastikan bahwa data yang dihapus adalah satu data.

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  // create many
  it("should create many records", async () => {
    const { count } = await prismaClient.customer.createMany({
      data: [
        {
          id: "alex",
          name: "alex",
          email: "alex@gmail.com",
          phone: "8922328282,",
        },
        {
          id: "karsa",
          name: "karsa",
          email: "karsa@gmail.com",
          phone: "292828282,",
        },
      ],
    });
    expect(count).toBe(2);
  });

  // update many
  it("should be can update many records", async () => {
    const { count } = await prismaClient.customer.updateMany({
      data: {
        email: "alexlagi@gmail.com",
      },
      where: {
        name: "alex",
      },
    });
    expect(count).toBe(1);
  });

  // delete many
  it("should can delete many records", async () => {
    const count = await prismaClient.customer.delete({
      where: {
        id: "karsa",
      },
    });
  });

  // read many
  it("should can read many records", async () => {
    const customers = await prismaClient.customer.findMany({});
    console.info(customers);
    expect(customers.length).toBe(6);
  });
});
```

**Selanjutnya :** [Paging](paging.md)
