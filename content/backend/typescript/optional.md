---
title: Optional Properties
tags:
  - typescript
---

# Optional Properties

- Secara default, saat kita membuat attribute di Object atau Type, maka attribute tersebut wajib diisi nilainya.
- Namun, tidak semua attribute itu wajib diisi nilainya
- Pada kasus attribute yang tidak wajib diisi nilainya, kita bisa tambahkan tanda ? untuk menandakan bahwa itu adalah optional properties.

## Kode: Optional Properties

```js
export type Category = {
  id: string,
  name: string,
  description?: string,
};

export type Product = {
  id: string,
  name: string,
  price: number,
  category: Category,
  description?: string,
};

const person: { id: string, name: string, hobbies?: string[] } = {
  id: "1",
  name: "Nay",
};

console.info(person);
person.id = "2";
person.name = "Inayah";
```

**Selanjutnya** : [Enum](/backend/typescript/enum.md)
