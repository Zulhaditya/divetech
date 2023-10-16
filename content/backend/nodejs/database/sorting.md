---
title: Sorting
tags:
  - database
---

- Method findMany() juga memiliki parameter orderBy untuk mengurutkan datanya.
- Kita bisa tentukan apakah akan diurutkan berdasarkan asc atau desc.

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can do sorting", async () => {
    const customers = await prismaClient.customer.findMany({
      skip: 0,
      take: 10,
      orderBy: [
        {
          name: "desc",
        },
        {
          email: "asc",
        },
      ],
    });
    console.info(customers);
  });
});
```

**Selanjutnya :** [Select Fields](selectfields.md)