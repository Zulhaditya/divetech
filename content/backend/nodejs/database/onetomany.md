---
title: One to Many
tags:
  - database
---

- Relasi one to many sebenarnya mirip dengan one to one, yang membedakannya adalah di table yang memiliki join column, tidak terdapat aturan unique, sehingga bisa lebih dari satu kali.
- Contoh kasus misalkan Customer dengan Comment, dimana Customer bisa membuat banyak data Comment.
- Sehingga dari Customer ke Comment adalah relasi one to many, sedangkan kebalikannya adalah relasi many to one.
- Untuk menambah informasi one to many, sama seperti one to one, menggunakan @relation(), namun tipe datanya perlu ditambahkan [ ] sebagai penanda bahwa itu array/list.

# Example

## 1 - Buat table comments dan insert data

```sql
CREATE TABLE
comments (
id INT NOT NULL AUTO_INCREMENT,
customer_id VARCHAR(100) NOT NULL,
title VARCHAR(100) NOT NULL,
deskripsi text,
PRIMARY KEY (id),

CONSTRAINT comments_customer_id_fk FOREIGN KEY (customer_id) REFERENCES customers (id)
) engine INNODB;

INSERT INTO
comments (customer_id, title, deskripsi) VALUE ('rio', 'Comment 1', 'Sample comment 1'),
('rio', 'Comment 2', 'Sample comment 2'),
('rodol', 'Comment 1', 'Sample comment 1'),
('rodol', 'Comment 2', 'Sample comment 2')
```

## 2 - Buat model Customer dan Comment di Prisma Schema

```js
model Customer {
id String @id @db.VarChar(100)
name String
email String @unique
phone String @unique
wallet Wallet?
comments Comment[]

@@map("customers")
}

model Comment {
id Int @id @default(autoincrement())
title String @db.VarChar(200)
deskripsi String? @db.Text
customer_id String @db.VarChar(100)
customer Customer @relation(fields: [customer_id], references: [id])

@@map("comments")
}

```

## 3 - Buat unit testing

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  it("should can insert and include", async () => {
    const comment = await prismaClient.comment.create({
      data: {
        customer_id: "rio",
        title: "Insert Comment",
        deskripsi: "Deskripsi Comment",
      },
      include: {
        customer: true,
      },
    });
    console.info(comment);
  });

  it("should can insert and many relation", async () => {
    const customer = await prismaClient.customer.create({
      data: {
        id: "apis",
        name: "Apis",
        email: "apis@gmail.com",
        phone: "8928282882",
        comments: {
          createMany: {
            data: [
              {
                title: "Comment 1",
                deskripsi: "Deskripsi 1",
              },
              {
                title: "Comment 2",
                deskripsi: "Deskripsi 2",
              },
            ],
          },
        },
      },
      include: {
        comments: true,
      },
    });
    console.info(customer);
  });

  it("should can find many with filter relation", async () => {
    const customers = await prismaClient.customer.findMany({
      where: {
        comments: {
          some: {
            title: {
              contains: "Comment",
            },
          },
        },
      },
      include: {
        comments: true,
      },
    });
    console.info(JSON.stringify(customers));
  });
});
```

**Selanjutnya :** [Many to Many](manytomany.md)
