---
title: Many to Many
tags:
  - database
---

- Jenis relasi terakhir yang paling kompleks adalah Many to Many.
- Untuk Many to Many, kita juga bisa melakukan di Prisma Schema.
- Relasi Many to Many membutuhkan table penghubung, sehingga kita perlu membuat table penghubung terlebih dahulu.
- Sekarang, kita akan coba membuat relasi dari Customer ke Product, misalkan kita akan buat fitur likes, dimana satu product bisa dilike oleh banyak customer, dan satu customer juga bisa like banyak product.

# Example

## 1 - Buat table like

```sql
CREATE TABLE
likes (
customer_id VARCHAR(100) NOT NULL,
product_id VARCHAR(100) NOT NULL,
PRIMARY KEY (customer_id, product_id),

CONSTRAINT likes_customer_id_fk FOREIGN KEY (customer_id) REFERENCES customers (id),
CONSTRAINT likes_product_id_fk FOREIGN KEY (product_id) REFERENCES products (id)
) engine INNODB;
```

## 2 - Buat model customer, product, dan like

```js
model Customer {
id String @id @db.VarChar(100)
name String
email String @unique
phone String @unique
wallet Wallet?
comments Comment[]
likes Like[]

@@map("customers")
}

model Product {
id String @id
name String
price Int
stock Int
category String
likedBy Like[]

@@map("products")
}

model Like {
customer_id String @db.VarChar(100)
product_id String @db.VarChar(100)
customer Customer @relation(fields: [customer_id], references: [id])
product Product @relation(fields: [product_id], references: [id])

@@id([customer_id, product_id])
@@map("likes")
}
```

## 3 - Buat unit testing

```js
it("should can insert many to many relation", async () => {
  const like = await prismaClient.like.create({
    data: {
      customer_id: "apis",
      product_id: "P0001",
    },
    include: {
      customer: true,
      product: true,
    },
  });
  console.info(like);
});

it("should can find one with many to many relation", async () => {
  const customer = await prismaClient.customer.findUnique({
    where: {
      id: "rio",
    },
    include: {
      likes: {
        include: {
          product: true,
        },
      },
    },
  });
  console.info(JSON.stringify(customer, null, 2));
});

it("should can find many with many to many relation", async () => {
  const customers = await prismaClient.customer.findMany({
    where: {
      likes: {
        some: {
          product: {
            name: {
              contains: "A",
            },
          },
        },
      },
    },
    include: {
      likes: {
        include: {
          product: true,
        },
      },
    },
  });
  console.info(JSON.stringify(customers, null, 2));
});
```

# Implicit Many to Many Relationship

- Sebelumnya saat membuat relasi Many to Many, kita menyebutkan model untuk tabel penghubungnya, atau dibilang explicit many to many.
- Prisma juga memiliki fitur implicit many to many, dimana kita tidak perlu menyebutkan model penghubungnya.
- Namun untuk fitur implicit many to many, ada aturannya.
- Nama table harus \_ diikuti nama relasi, dan nama kolom harus A dan B, dimana A adalah kolom model pertama, dan B adalah kolom model kedua, diurutkan secara asc nama modelnya.
- Misalkan kita akan coba buat relasi lagi many to many dari Customer ke Product untuk fitur Loves.

## 1 - Buat tabel loves

```sql
CREATE TABLE
_loves (
A VARCHAR(100) NOT NULL,
B VARCHAR(100) NOT NULL,
PRIMARY KEY (A, B),

CONSTRAINT customer_loves_fk FOREIGN KEY (A) REFERENCES customers (id),
CONSTRAINT product_loves_fk FOREIGN KEY (B) REFERENCES products (id)
) engine INNODB;
```

## 2 - Buat model customer, product, dan loves

```js
model Customer {
id String @id @db.VarChar(100)
name String
email String @unique
phone String @unique
wallet Wallet?
comments Comment[]
likes Like[]
loves Product[] @relation("loves")

@@map("customers")
}

model Product {
id String @id
name String
price Int
stock Int
category String
likedBy Like[]
lovedBy Customer[] @relation("loves")

@@map("products")
}
```

## 3 - Buat unit test

```js
it("should can create implicit relation", async () => {
  const customer = await prismaClient.customer.update({
    where: {
      id: "rio",
    },
    data: {
      loves: {
        connect: [
          {
            id: "P0001",
          },

          {
            id: "P0002",
          },
        ],
      },
    },
    include: {
      loves: true,
    },
  });
  console.info(customer);
});

it("should can find many implicit relation", async () => {
  const customers = await prismaClient.customer.findMany({
    where: {
      loves: {
        some: {
          name: {
            contains: "A",
          },
        },
      },
    },
    include: {
      loves: true,
    },
  });
  console.info(customers);
});
```

**Selanjutnya :** [Prisma Migrate](prismamigrate.md)
