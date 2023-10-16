---
title: Count
tags:
  - database
---

- Prisma Client memiliki method untuk melakukan query aggregate count dengan method count().
- Cara penggunaannya mirip dengan method findMany().

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can count", async () => {
    const total = await prismaClient.customer.count({
      where: {
        name: "Goku",
      },
    });
    expect(total).toBe(3);
  });
});
```

**Selanjutnya :** [Aggregate](aggregate.md)
