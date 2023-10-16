---
title: Where Condition
tags:
  - database
---

- Sampai saat ini, kita hanya melakukan operasi equals (=) ketika melakukan query ke database.
- Prisma Client mendukung banyak sekali where condition dan operator, yang bisa kita gunakan untuk membuat query secara flexible.
- Semua condition dan operator yang didukung bisa dilihat di halaman dokumentasinya.
- https://www.prisma.io/docs/reference/api-reference/prisma-client-reference#filter-conditions-and-operators

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can using OR operator", async () => {
    const products = await prismaClient.product.findMany({
      where: {
        OR: [
          {
            name: "A",
          },
          {
            name: "B",
          },
        ],
      },
      orderBy: [
        {
          name: "asc",
        },
      ],
    });
    console.info(products);
    expect(products.length).toBe(4);
    expect(products[0].name).toBe("A");
    expect(products[1].name).toBe("A");
    expect(products[2].name).toBe("B");
    expect(products[3].name).toBe("B");
  });
});
```

**Selanjutnya :** [Prisma Schema](prismaschema.md)
