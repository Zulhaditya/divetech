---
title: Aggregate
tags:
  - database
---

- Kita tau bahwa function aggregate di database tidak hanya count, bagaimana dengan penerapan function aggregate lainnya?
- Prisma Client menyediakan method aggregate() yang bisa digunakan untuk melakukan query aggregate.

# Example

## 1- Buat table products dan Insert data ke database

```sql
CREATE TABLE
products (
id VARCHAR(100) NOT NULL,
name VARCHAR(100) NOT NULL,
price INT NOT NULL,
stock INT NOT NULL,
category VARCHAR(100) NOT NULL,
PRIMARY KEY (id)
) engine INNODB;

SELECT * FROM products;

INSERT INTO products (id, name, price, stock, category) VALUE ('P0001', 'A', 1000, 100, 'K1'),
('P0002', 'B', 2000, 200, 'K1'),
('P0003', 'C', 3000, 300, 'K1'),
('P0004', 'D', 4000, 400, 'K1'),
('P0005', 'E', 5000, 500, 'K1');

SELECT * FROM products;
```

## 2- Buat model schema prisma

```js
model Product {
id String @id
name String
price Int
stock Int
category String

@@map("products")
}
```

# Function Aggregate

- Berikut adalah beberapa function aggregate yang didukung oleh Prisma Client:
- **\_count, \_min, \_max, \_sum, \_avg**
- Lantas bagaimana dengan function aggregate lainnya? Kita harus lakukan manual menggunakan **Raw SQL.**

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can do aggregate function", async () => {
    const result = await prismaClient.product.aggregate({
      _min: {
        price: true,
        stock: true,
      },
      _max: {
        price: true,
        stock: true,
      },
      _avg: {
        price: true,
        stock: true,
      },
    });
    console.info(result);
  });
});
```

# Group By

- Saat menggunakan function aggregate, kita butuh melakukan GROUP BY.
- Pada kasus ini, kita bisa menggunakan function **groupBy()**, tidak menggunakan function aggregate() lagi.

```js
it("should can do aggregate function with group by", async () => {
  const result = await prismaClient.product.groupBy({
    by: ["category"],
    _min: {
      price: true,
      stock: true,
    },
    _max: {
      price: true,
      stock: true,
    },
    _avg: {
      price: true,
      stock: true,
    },
  });
  console.info(result);
});
```

# Having

- Pada method groupBy() juga terdapat attribute having yang bisa digunakan untuk kondisi HAVING pada SQL Query yang akan kita lakukan.

```js
it("should can do aggregate function with group by and having", async () => {
  const result = await prismaClient.product.groupBy({
    by: ["category"],
    _min: {
      price: true,
      stock: true,
    },
    _max: {
      price: true,
      stock: true,
    },
    _avg: {
      price: true,
      stock: true,
    },
    having: {
      price: {
        _avg: {
          gt: 2000,
        },
      },
    },
  });
  console.info(result);
});
```

**Selanjutnya :** [Where](wherecondition.md)
