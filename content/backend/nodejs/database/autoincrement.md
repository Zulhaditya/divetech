---
title: Auto Increment
tags:
  - database
---

- Beberapa database biasanya mendukung fitur auto increment pada Primary Key, seperti MySQL dan PostgreSQL.
- Kita bisa memberitahu Prisma Schema bahwa field tersebut mempunyai fitur auto increment, sehingga kita tidak wajib memasukkan datanya ketika menggunakan Prisma Client.
- Kita cukup gunakan attribute @default() dan pilih jenis auto increment yang tersedia.
- https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#attribute-functions

# Example

## 1 - Buat tabel categories

```sql
CREATE TABLE
categories (
id INT NOT NULL AUTO_INCREMENT,
name VARCHAR(100) NOT NULL,
PRIMARY KEY (id)
) engine INNODB;
```

## 2 - Buat model categories di Prisma Schema

```js
model Category {
id Int @id @default(autoincrement())
name String @db.VarChar(100)

@@map("categories")
}
```

## 3 - Buat unit testing

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should be able to create with auto increment primary key", async () => {
    const category = await prismaClient.category.create({
      data: {
        name: "Food",
      },
    });
    console.info(category);
    expect(category).toHaveProperty("id");
  });
});
```

**Selanjutnya :** [One to One](onetoone.md)
