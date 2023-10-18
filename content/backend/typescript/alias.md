---
title: Type Alias
tags:
  - typescript
---

# Type Alias

- Menggunakan tipe data any sebenarnya tidak direkomendasikan.
- Biasanya ketika menggunakan tipe data any, jika kita menggunakan library dari orang lain yang tidak bisa diubah tipe datanya.
- Jika kita membuat tipe data JavaScript object sendiri, kita bisa membuat alias untuk struktur tipe data objectnya.

## Kode: Alias

```js
export type Category = {
  id: string,
  name: string,
};

export type Product = {
  id: string,
  name: string,
  price: number,
  category: Category,
};
```

## Kode: Test Alias

```js
const category: Category = {
  id: "1",
  name: "Handphone",
};

const product: Product = {
  id: "1",
  name: "Samsung S20",
  price: 20000000,
  category: category,
};

console.info(category);
console.info(product);
```

## Kode: Type Alias untuk Union

```js
export type ID = string | number;

export type Category = {
  id: ID,
  name: string,
};

export type Product = {
  id: ID,
  name: string,
  price: number,
  category: Category,
};
```

**Selanjutnya** : [Object](/backend/typescript/object.md)
