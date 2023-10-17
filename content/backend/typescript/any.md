---
title: Any
tags:
  - typescript
---

# Tipe Data Any

- Saat menggunakan TypeScript idealnya kita membuat deklarasi datanya.
- Contoh, saat menggunakan JavaScript object, idealnya harus ada attribute yang dimiliki, sedangkan pada JavaScript hal tersebut tidak diwajibkan.
- Jika kita ingin membuat tipe data yang bebas seperti JavaScript, kita bisa gunakan tipe data any.
- Tipe data any tidak akan dicheck oleh TypeScript pada akses data tersebut.

## Kode: Tipe Data Any

```js
const person: any = {
  id: 1,
  name: "Zulhaditya",
  age: 27,
};

person.age = 30;
console.info(person);
```

**Selanjutnya** : [Union](/backend/typescript/union.md)
