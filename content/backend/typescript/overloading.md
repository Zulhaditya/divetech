---
title: Function Overloading
tags:
  - typescript
---

# Function Overloading

- Function overloading adalah kemampuan untuk membuat function dengan nama yang sama, namun dengan parameter input yang berbeda.
- Di JavaScript, membuat satu function dengan input data yang berbeda dan output yang berbeda sudah biasa untuk dilakukan.
- Namun, hal ini bisa membuat sebuah function tidak aman, karena bisa menghasilkan hasil yang berbeda-beda tiap data.
- TypeScript memberikan kemampuan function overloading, agar pembuatan function seperti ini lebih aman untuk dilakukan.

## Kode: Function Overloading

```js
function callMe(value: number): number;
function callMe(value: string): string;
function callMe(value: any) {
  if(typeof value === "string") {
    return value;
  } else if (typeof value === "number") {
    return value;
  }
}

expect(callMe(100)).toBe(100)
expect(callMe("Nay")).toBe("Nay")

```

**Selanjutnya** : [Function as Parameter](/backend/typescript/funcparameter.md)
