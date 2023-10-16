---
title: One to One
tags:
  - database
---

- Ketika membuat table dengan relasi one to one, kita juga perlu memberitahu di Prisma Schema.
- Hal ini dilakukan agar urusan join bisa dilakukan secara otomatis oleh Prisma Client.
- Untuk membuat relasi one to one, kita bisa menggunakan @relation dan ditempatkan di model yang melakukan join column-nya.

# Relation Operator

- Ketika kita mau melakukan Read data untuk relasi, kita bisa gunakan relation operator.
- Namun kita harus cek jenis relasi, contoh beberapa operator hanya bisa untuk relasi To Many misalnya.
- https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#relation-filters

# Example

## 1 - Buat table wallet

```sql
CREATE TABLE
wallet (
id VARCHAR(100) NOT NULL,
balance INT NOT NULL,
customer_id VARCHAR(100) NOT NULL,
PRIMARY KEY (id),

CONSTRAINT wallet_customer_id_fk FOREIGN KEY (customer_id) REFERENCES customers (id),
CONSTRAINT wallet_customer_id_unique UNIQUE (customer_id)
) engine INNODB;
```

## 2 - Buat model Customer dan Wallet di Prisma Schema

```js
model Customer {
id String @id @db.VarChar(100)
name String
email String @unique
phone String @unique
wallet Wallet?

@@map("customers")
}

model Wallet {
id String @id @db.VarChar(100)
balance Int @db.Int
customer_id String @unique @db.VarChar(100)
customer Customer @relation(fields: [customer_id], references: [id])

@@map("wallet")
}
```

## 3 - Buat unit testing

```js
import { prismaClient } from "../src/prisma-client";

describe("Prisma Client", () => {
  // buat data wallet yang include dengan table customer
  it("should can create one to one relation", async () => {
    const wallet = await prismaClient.wallet.create({
      data: {
        id: "rio",
        customer_id: "rio",
        balance: 1000000,
      },
      include: {
        customer: true,
      },
    });
    console.info(wallet);
  });

  // buat data customer yang include dengan table wallet
  it("should can create one to one with relation", async () => {
    const customer = await prismaClient.customer.create({
      data: {
        id: "rodol",
        name: "Rodol",
        email: "rodol@gmail.com",
        phone: "09871616161",
        wallet: {
          create: {
            id: "rodol",
            balance: 500000,
          },
        },
      },
      include: {
        wallet: true,
      },
    });
    console.info(customer);
  });

  // cari data di customer beserta data di table walletnya
  it("should can find one to one with relation", async () => {
    const customer = await prismaClient.customer.findUnique({
      where: {
        id: "rodol",
      },
      include: {
        wallet: true,
      },
    });
    console.info(customer);
  });

  // cari data customer yang hanya memiliki data wallet
  it("should can find one to one with relation filter", async () => {
    const customers = await prismaClient.customer.findMany({
      where: {
        wallet: {
          isNot: null,
        },
      },
      include: {
        wallet: true,
      },
    });
    console.info(customers);
  });
});
```

**Selanjutnya :** [One to Many](onetomany.md)
