---
title: Enum
tags:
  - typescript
---

# Enum

- TypeScript memiliki tipe data enum, yaitu tipe data yang nilainya sudah pasti.
- Tipe data ini tidak dimiliki oleh JavaScript.
- Secara default, tipe data enum akan dikonversi menjadi **string** di JavaScript, namun juga bisa dikonversi menjadi **number**.

## Kode: Enum

```js
export enum CustomerType {
  REGULAR,
  GOLD,
  PLATINUM
}

export type Customer = {
  id: number;
  name: string;
  type: CustomerType
}
```

## Kode: Menggunakan Enum

```js
const customer: Customer = {
  id: 1,
  name: "Nay",
  type: CustomerType.GOLD,
};

console.info(customer);
```

# Enum di TypeScript

- Secara default, enum di TypeScript akan dikonversi menjadi tipe data number.
- Kadang kita ingin mengubah dari number menjadi string, kita bisa lakukan hal ini ketika membuat enum-nya.

## Kode: Enum sebagai String

```js
export enum CustomerType {
  REGULAR = 'REGULAR',
  GOLD = 'GOLD',
  PLATINUM = 'PLATINUM'
}

export type Customer = {
  id: number;
  name: string;
  type: CustomerType
}
```

**Selanjutnya** : [Null](/backend/typescript/null.md)
