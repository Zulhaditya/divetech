---
title: Object
tags:
  - typescript
---

# Object Type

- Pada kasus yang sederhana, membuat alias itu terlalu memakan waktu. Kita bisa membuat tipe data JavaScript secara langsung dengan melakukan deklarasi variable secara langsung pada object.
- Hal ini lebih sederhana dibandingkan membuat type terlebih dahulu.

## Kode: Object Type

```js
const person: { id: string, name: string } = {
  id: "1",
  name: "Nay",
};

console.info(person);

person.id = "2";
person.name = "Inayah";

console.info(person);
```

**Selanjutnya** : [Optional](/backend/typescript/optional.md)
