---
title: Paging
tags:
  - database
---

- Method findMany() di Prisma Client juga mendukung paging menggunakan parameter skip dan take.
- Take adalah jumlah maksimal data yang diambil.
- Skip adalah jumlah data yang akan di skip di awal.

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can do paging", async () => {
    const page1 = await prismaClient.customer.findMany({
      skip: 0,
      take: 1,
    });
    expect(page1.length).toBe(1);

    const page2 = await prismaClient.customer.findMany({
      skip: 1,
      take: 1,
    });
    expect(page2.length).toBe(1);

    const page3 = await prismaClient.customer.findMany({
      skip: 2,
      take: 1,
    });
    expect(page3.length).toBe(1);
  });
});
```

**Selanjutnya :** [Sorting](sorting.md)
